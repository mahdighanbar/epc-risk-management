# Complete Payment Approval Workflow Test

Follow these steps to test the complete workflow with only 1 approval required.

## 📊 Current Setup

✅ Project created and funded
✅ Consultant added
✅ Required approvals: **1** (changed from 2)

---

## 🎬 Step-by-Step Test

### Step 1: Request Payment (As Contractor)

**Account:** Contractor (`0x70997970C51812dc3A010C7d01b50e0d17dc79C8`)

1. **Import account into MetaMask:**
   - Private key: `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d`

2. **Switch to contractor account** in MetaMask

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show: 🔨 **Contractor** (green badge)

5. **Go to Payments page**

6. **Click "Request Payment"**

7. **Fill in form:**
   - Recipient Address: `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` (your own address)
   - Amount: `5` ETH
   - Description: `Test Payment - Phase 1`

8. **Click "Request Payment"**

9. **Approve in MetaMask**

10. **Wait for confirmation**

**✅ Expected Result:**
- Success message appears
- New payment request shows in list
- Status: "Pending Approval"
- Approvals: 0/1

---

### Step 2: Approve Payment (As Consultant)

**Account:** Consultant (`0x90F79bf6EB2c4f870365E785982E1f101E93b906`)

1. **Import account into MetaMask:**
   - Private key: `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6`

2. **Switch to consultant account** in MetaMask

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show: ✅ **Consultant** (purple badge)

5. **Go to Payments page**

6. **Find the payment request** you just created

7. **Open browser console** (F12) to see debug logs

8. **Click "Approve" button**

9. **Approve in MetaMask**

10. **Wait for confirmation**

**✅ Expected Result:**
- Console shows: "🔵 Approving payment request: 1"
- Console shows: "🔵 Transaction sent: 0x..."
- Console shows: "✅ Payment approved!"
- Success toast appears
- Approvals: 1/1
- Status changes to: "Ready to Execute" (yellow badge)

---

### Step 3: Execute Payment (As Project Manager)

**Account:** Project Manager (`0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC`)

1. **Import account into MetaMask** (if not already):
   - Private key: `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a`

2. **Switch to project manager account** in MetaMask

3. **Refresh browser** (F5)

4. **Check Dashboard:**
   - Should show: 📋 **Project Manager** (blue badge)

5. **Go to Payments page**

6. **Find the approved payment request**
   - Should show status: "Ready to Execute"
   - Should see "Execute" button

7. **Click "Execute" button**

8. **Approve in MetaMask**

9. **Wait for confirmation**

**✅ Expected Result:**
- Success toast appears
- Status changes to: "Executed" (green badge)
- 5 ETH transferred to contractor
- Payment marked as complete

---

### Step 4: Verify (As Contractor)

**Account:** Contractor (`0x70997970C51812dc3A010C7d01b50e0d17dc79C8`)

1. **Switch back to contractor account** in MetaMask

2. **Check MetaMask balance**
   - Balance should have increased by ~5 ETH (minus gas fees you paid for requesting)

3. **Go to Payments page**
   - Payment request shows as "Executed"

**✅ Expected Result:**
- Contractor received the funds
- Payment cannot be executed again

---

## 🐛 Troubleshooting

### Issue 1: "You need CONSULTANT role to approve payments"

**Cause:** You're not logged in as consultant OR consultant wasn't added properly

**Fix:**
1. Make sure you're on consultant account: `0x90F79bf6EB2c4f870365E785982E1f101E93b906`
2. Check if consultant was added: Run `npx hardhat run scripts/check-roles.js --network localhost`
3. If consultant shows "❌ No Consultant Role", re-run setup: `npx hardhat run scripts/quick-setup.js --network localhost`

---

### Issue 2: "Failed to approve payment"

**Open console (F12) and check for:**

**Error: "already approved"**
- You already approved this payment
- Switch to a different account to test

**Error: "not exists"**
- Payment request ID doesn't exist
- Make sure payment was created successfully

**Error: "already executed"**
- Payment was already executed
- Create a new payment request to test again

---

### Issue 3: Can't Execute Payment - No Button

**Cause:** Payment doesn't have enough approvals yet

**Check:**
- Approvals shows: 1/1 (should be full)
- Status shows: "Ready to Execute" (yellow)
- If not, approve the payment first

---

### Issue 4: Execute Button Appears But Transaction Fails

**Cause:** You're not the project manager

**Fix:**
1. Switch to project manager account: `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC`
2. Refresh browser
3. Try again

---

## 📊 Test Checklist

After completing all steps:

- [ ] Contractor could request payment
- [ ] Payment request visible on Payments page
- [ ] Consultant could approve payment (1 approval required)
- [ ] Approval count increased to 1/1
- [ ] Status changed to "Ready to Execute"
- [ ] Project Manager could execute payment
- [ ] Funds transferred successfully
- [ ] Payment marked as executed
- [ ] Contractor balance increased

---

## 🎉 Success Criteria

Your workflow is working correctly if:

✅ All roles were detected correctly on Dashboard
✅ Each role could only perform their allowed actions
✅ Payment required only 1 approval (not 2)
✅ Funds transferred correctly
✅ No console errors during the process

---

## 🚀 Next Steps

Once this works:

1. Test with multiple payment requests
2. Test error cases (insufficient funds, wrong roles, etc.)
3. Test document upload functionality
4. Test project completion workflow
5. Consider deploying to Sepolia testnet for public testing

---

**Good luck! Follow each step carefully and check the console for any errors.** 🎯
