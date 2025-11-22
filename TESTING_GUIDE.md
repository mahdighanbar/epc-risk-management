# Complete Testing Guide for EPC Project Manager

This guide will walk you through testing all features of your DApp.

## 📋 Test Accounts Setup

You have 4 roles to test. Use these Hardhat accounts:

| Role | Address | Private Key |
|------|---------|-------------|
| **Admin** | `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266` | `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` |
| **Contractor** | `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` | `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d` |
| **Project Manager** | `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC` | `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a` |
| **Consultant** | `0x90F79bf6EB2c4f870365E785982E1f101E93b906` | `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6` |

---

## 🎯 Test Scenario: Complete Project Workflow

### Phase 1: Admin Creates Project

**As Admin (Account #0):**

1. ✅ **Already connected** with admin account
2. **Go to Projects page**
3. **Click "Create Project"**
4. **Fill in:**
   - Project Name: `Construction Site Alpha`
   - Contractor Address: `0x70997970C51812dc3A010C7d01b50e0d17dc79C8`
   - Project Manager Address: `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC`
   - Budget: `100` ETH
5. **Click "Create Project"**
6. **Approve in MetaMask**
7. **Wait for confirmation**

**Expected Result:**
- ✅ Success notification
- ✅ New project appears in projects list
- ✅ Project ID: 1
- ✅ Status: Active

---

### Phase 2: Admin Adds Consultant

**Still as Admin:**

1. **Go to Team page**
2. **Click "Add Team Member"** or similar
3. **Select Project:** `Construction Site Alpha`
4. **Select Role:** `Consultant`
5. **Enter Address:** `0x90F79bf6EB2c4f870365E785982E1f101E93b906`
6. **Click "Add"**
7. **Approve in MetaMask**

**Expected Result:**
- ✅ Consultant added successfully
- ✅ Consultant can now approve payments

---

### Phase 3: Admin Funds the Project

**Still as Admin:**

1. **Go to Projects page**
2. **Click on "Construction Site Alpha"** project
3. **Find "Fund Project" section**
4. **Enter amount:** `50` ETH
5. **Click "Fund"**
6. **Approve in MetaMask**

**Expected Result:**
- ✅ Project balance shows 50 ETH
- ✅ Transaction confirmed

---

### Phase 4: Contractor Uploads Document

**Switch to Contractor (Account #1):**

1. **In MetaMask:** Click account icon → Import Account
2. **Paste private key:** `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d`
3. **Switch to this account**
4. **Refresh browser** (F5)
5. **Connect wallet**
6. **Go to Documents page**
7. **Click "Upload Document"**
8. **Fill in:**
   - Project: `Construction Site Alpha`
   - Document Title: `Building Plans v1.0`
   - IPFS Hash: `QmTest123456789` (fake for testing)
   - Description: `Initial building plans`
9. **Click "Upload"**
10. **Approve in MetaMask**

**Expected Result:**
- ✅ Document uploaded successfully
- ✅ Document appears in documents list

---

### Phase 5: Contractor Requests Payment

**Still as Contractor:**

1. **Go to Payments page**
2. **Click "Request Payment"**
3. **Fill in:**
   - Project: `Construction Site Alpha`
   - Amount: `10` ETH
   - Recipient Address: `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` (your own address)
   - Description: `Payment for Phase 1 completion`
4. **Click "Request"**
5. **Approve in MetaMask**

**Expected Result:**
- ✅ Payment request created
- ✅ Request ID: 1
- ✅ Status: Pending Approval
- ✅ Approvals: 0/2

---

### Phase 6: Consultant Approves Payment

**Switch to Consultant (Account #3):**

1. **In MetaMask:** Import Account → Paste: `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6`
2. **Switch to consultant account**
3. **Refresh browser**
4. **Connect wallet**
5. **Go to Payments page**
6. **Find payment request #1**
7. **Click "Approve"**
8. **Approve in MetaMask**

**Expected Result:**
- ✅ Approval recorded
- ✅ Approvals: 1/2
- ✅ Status: Partially Approved

---

### Phase 7: Second Approval (Admin as Consultant)

**Switch back to Admin (Account #0):**

1. **In MetaMask:** Switch to admin account
2. **Refresh browser**
3. **Go to Payments page**
4. **Find payment request #1**
5. **Click "Approve"** (admin can also act as consultant)
6. **Approve in MetaMask**

**Expected Result:**
- ✅ Second approval recorded
- ✅ Approvals: 2/2
- ✅ Status: Approved (Ready for Execution)

---

### Phase 8: Project Manager Executes Payment

**Switch to Project Manager (Account #2):**

1. **In MetaMask:** Import Account → Paste: `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a`
2. **Switch to project manager account**
3. **Refresh browser**
4. **Connect wallet**
5. **Go to Payments page**
6. **Find payment request #1** (should show as approved)
7. **Click "Execute Payment"**
8. **Approve in MetaMask**

**Expected Result:**
- ✅ Payment executed
- ✅ 10 ETH transferred to contractor
- ✅ Project balance reduced by 10 ETH (now 40 ETH)
- ✅ Status: Completed
- ✅ Contractor balance increased by 10 ETH

---

### Phase 9: Project Manager Completes Project

**Still as Project Manager:**

1. **Go to Projects page**
2. **Click on "Construction Site Alpha"**
3. **Click "Complete Project"** button
4. **Confirm in dialog**
5. **Approve in MetaMask**

**Expected Result:**
- ✅ Project status: Completed
- ✅ Project is no longer active
- ✅ Can view project history

---

## 🧪 Additional Tests

### Test Access Controls

Try these to verify security:

1. **As Contractor:** Try to execute a payment → Should FAIL ❌
2. **As Consultant:** Try to request a payment → Should FAIL ❌
3. **As Random User:** Try to create a project → Should FAIL ❌
4. **As Admin:** Try to upload document → Should FAIL ❌ (only contractor can)

---

## 📊 Verification Checklist

After completing all phases, verify:

- [ ] Project created successfully
- [ ] Consultant added to project
- [ ] Project funded (shows correct balance)
- [ ] Document uploaded (visible in Documents page)
- [ ] Payment requested by contractor
- [ ] Payment approved by 2 consultants
- [ ] Payment executed by project manager
- [ ] Funds transferred correctly
- [ ] Project completed successfully
- [ ] All events logged (check browser console)

---

## 🔍 Where to Check Results

### 1. Browser Debug Box (Bottom Right)
Shows: Account, Role, Chain ID, Contract connection

### 2. Browser Console (F12)
Shows: Transaction hashes, events, errors

### 3. Hardhat Node Terminal
Shows: Transaction logs, gas usage, blocks

### 4. MetaMask Activity
Shows: All transactions, confirmations, balances

---

## 🐛 Common Issues During Testing

### "Transaction Failed"
- Check you're using the correct role
- Verify account has ETH for gas
- Check contract state (e.g., payment already approved)

### "Insufficient Balance"
- Make sure project has enough funds
- Check escrow balance for payment requests

### "Not Authorized"
- Verify you're using correct account for the action
- Check role assignments in Team page

### Button Not Appearing
- Verify you're connected with correct account
- Check debug box shows correct role
- Refresh browser after switching accounts

---

## 📝 Testing Notes Template

Use this to track your testing:

```
Test Date: ___________
Tester: ___________

Phase 1 - Create Project: ✅ / ❌
  Transaction Hash: ___________
  Project ID: ___________

Phase 2 - Add Consultant: ✅ / ❌
  Transaction Hash: ___________

Phase 3 - Fund Project: ✅ / ❌
  Amount: ___________
  Transaction Hash: ___________

Phase 4 - Upload Document: ✅ / ❌
  Document ID: ___________
  Transaction Hash: ___________

Phase 5 - Request Payment: ✅ / ❌
  Request ID: ___________
  Amount: ___________

Phase 6 - Approve Payment (Consultant): ✅ / ❌
  Transaction Hash: ___________

Phase 7 - Approve Payment (Admin): ✅ / ❌
  Transaction Hash: ___________

Phase 8 - Execute Payment: ✅ / ❌
  Transaction Hash: ___________
  Contractor Balance After: ___________

Phase 9 - Complete Project: ✅ / ❌
  Transaction Hash: ___________

Notes:
___________________________________________
___________________________________________
```

---

## 🎉 Success Criteria

Your DApp is working correctly if:

✅ All 9 phases completed without errors
✅ All role-based access controls working
✅ Funds transferred correctly
✅ Events logged properly
✅ UI updates after each transaction
✅ MetaMask shows correct balances
✅ No console errors

---

## 🚀 Next Steps After Testing

1. **Test edge cases** (insufficient funds, unauthorized access, etc.)
2. **Deploy to Sepolia testnet** for public testing
3. **Share with team** for feedback
4. **Document any bugs** found
5. **Consider security audit** before mainnet

---

**Good luck with testing! Follow each phase carefully and note any issues.** 🧪
