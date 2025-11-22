# Complete Payment Workflow Test Guide

This guide walks you through testing the complete payment approval workflow with multiple users.

## 📋 Prerequisites

Make sure you have:
- ✅ Hardhat node running
- ✅ Contract deployed
- ✅ At least one active project
- ✅ Project has funds in escrow

---

## 👥 Test Accounts

| Role | Address | Private Key |
|------|---------|-------------|
| **Admin** | `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266` | `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` |
| **Contractor** | `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` | `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d` |
| **Project Manager** | `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC` | `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a` |
| **Consultant** | `0x90F79bf6EB2c4f870365E785982E1f101E93b906` | `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6` |

---

## 🔄 Complete Workflow

### Phase 1: Setup (As Admin)

**Account:** Admin (`0xf39Fd...`)

1. **Make sure you have a project** with funds
   - If not, create one and fund it with at least 10 ETH

2. **Add Consultant using script:**
   ```bash
   npx hardhat run scripts/add-consultant.js --network localhost
   ```

   OR manually on website:
   - Go to Team page
   - Click "Add Consultant"
   - Enter Project ID and Consultant address
   - Submit

**Expected:** Consultant added successfully ✅

---

### Phase 2: Request Payment (As Contractor)

**Account:** Contractor (`0x70997...`)

1. **Import contractor account into MetaMask**
   - MetaMask → Import Account
   - Paste private key: `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d`

2. **Switch to contractor account**

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show role as "🔨 Contractor"

5. **Go to Payments page**

6. **Click "Request Payment"**

7. **Fill in:**
   - Project: Select your project
   - Amount: `5` ETH
   - Recipient: `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` (your own address)
   - Description: `Phase 1 Completion Payment`

8. **Submit and approve in MetaMask**

**Expected:**
- ✅ Payment request created
- ✅ Request ID: 1 (or next number)
- ✅ Status: Pending
- ✅ Approvals: 0/2

---

### Phase 3: First Approval (As Consultant)

**Account:** Consultant (`0x90F79...`)

1. **Import consultant account into MetaMask**
   - MetaMask → Import Account
   - Paste private key: `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6`

2. **Switch to consultant account**

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show role as "✅ Consultant"

5. **Go to Payments page**

6. **Find the payment request** you just created

7. **Click "Approve"** button

8. **Approve in MetaMask**

**Expected:**
- ✅ Approval recorded
- ✅ Approvals: 1/2
- ✅ Status: Partially Approved

---

### Phase 4: Second Approval (As Admin or Another Consultant)

**Account:** Admin (`0xf39Fd...`) OR add another consultant

**Note:** You need 2 approvals total. Admin can also act as consultant.

1. **Switch to admin account** in MetaMask

2. **Refresh browser** (F5)

3. **Go to Payments page**

4. **Find the payment request**

5. **Click "Approve"**

6. **Approve in MetaMask**

**Expected:**
- ✅ Second approval recorded
- ✅ Approvals: 2/2
- ✅ Status: Approved (Ready for Execution)

---

### Phase 5: Execute Payment (As Project Manager)

**Account:** Project Manager (`0x3C44C...`)

1. **Import project manager account into MetaMask** (if not already)
   - MetaMask → Import Account
   - Paste private key: `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a`

2. **Switch to project manager account**

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show role as "📋 Project Manager"

5. **Go to Payments page**

6. **Find the approved payment** (should show 2/2 approvals)

7. **Click "Execute Payment"** button

8. **Approve in MetaMask**

**Expected:**
- ✅ Payment executed
- ✅ 5 ETH transferred to contractor
- ✅ Status: Completed
- ✅ Project balance reduced

---

### Phase 6: Verify (Check Contractor Balance)

**Account:** Contractor (`0x70997...`)

1. **Switch back to contractor account**

2. **Check MetaMask balance**
   - Should have increased by 5 ETH (minus gas fees)

3. **Go to Payments page**
   - Payment should show as "Executed" or "Completed"

**Expected:**
- ✅ Contractor received the funds
- ✅ Payment marked as completed
- ✅ Cannot be executed again

---

## 📊 Verification Checklist

After completing all phases:

- [ ] Consultant was added successfully
- [ ] Contractor could request payment
- [ ] Payment request visible to all users
- [ ] First approval worked (Consultant)
- [ ] Second approval worked (Admin/Consultant)
- [ ] Payment showed as "Approved" after 2 approvals
- [ ] Project Manager could execute payment
- [ ] Funds transferred correctly
- [ ] Payment marked as completed
- [ ] Cannot execute the same payment twice

---

## 🎯 Quick Script Test

For automated testing, run:

```bash
npx hardhat run scripts/test-full-workflow.js --network localhost
```

This tests the entire workflow automatically!

---

## 🐛 Troubleshooting

### "Not authorized" error
- Verify you're using the correct account for each action
- Check role assignments on Team page

### "Not enough approvals" error
- Make sure you have exactly 2 approvals before executing
- Check Payments page for approval count

### "No funds" error
- Make sure project has been funded
- Check project balance on Projects page

### MetaMask doesn't show balance change
- Refresh MetaMask
- Switch to another network and back
- Check transaction on block explorer

---

## 📝 Expected Timeline

- **Setup:** 2 minutes
- **Request Payment:** 1 minute
- **First Approval:** 1 minute
- **Second Approval:** 1 minute
- **Execute Payment:** 1 minute
- **Verification:** 1 minute

**Total:** ~7 minutes for complete workflow

---

## 🎉 Success Criteria

Your payment workflow is working correctly if:

✅ All 6 phases completed without errors
✅ Each role could perform their actions
✅ Other roles couldn't perform unauthorized actions
✅ Funds transferred correctly
✅ Payment state updated properly
✅ Events logged correctly (check console)

---

**Ready to test? Start with Phase 1!** 🚀
