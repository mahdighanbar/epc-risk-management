# Quick Test - Verify Everything Works

## 🚀 Automated Backend Test

Run this to verify all smart contract functions work correctly:

```bash
npx hardhat run scripts/test-full-workflow.js --network localhost
```

This automated script will:
- ✅ Create a project
- ✅ Add consultant
- ✅ Fund the project
- ✅ Upload a document
- ✅ Request a payment
- ✅ Approve payment (2 approvals)
- ✅ Execute payment
- ✅ Complete project

**Expected:** All tests pass with ✅

---

## 🌐 Manual Frontend Test

### Quick 5-Minute Test

1. **Open your browser:** `http://localhost:3000`

2. **Check Debug Box (bottom right):**
   - Contract Address: `0x5FbDB...` ✅
   - Your Account: `0xf39Fd...` ✅
   - User Role: `admin` ✅
   - Chain ID: `31337` ✅

3. **Create a Project:**
   - Go to Projects page
   - Click "Create Project"
   - Fill in details
   - Submit and approve in MetaMask
   - **Result:** Project appears in list ✅

4. **Verify Project:**
   - Click on the project
   - Check all details are correct
   - **Result:** All info displayed ✅

5. **Fund the Project:**
   - Enter amount (e.g., 10 ETH)
   - Click "Fund"
   - Approve in MetaMask
   - **Result:** Balance updates ✅

---

## 🧪 Full Frontend Test

Follow the complete guide: `TESTING_GUIDE.md`

This includes:
- Testing all 4 user roles
- Complete payment workflow
- Document management
- Access control verification

**Time needed:** ~30 minutes

---

## 📊 Test Results Checklist

### Backend Test (Automated)
- [ ] All 10 tests pass
- [ ] No errors in console
- [ ] Transaction hashes shown
- [ ] Balances updated correctly

### Frontend Test (Manual)
- [ ] Can create project
- [ ] Can fund project
- [ ] Can upload document
- [ ] Can request payment
- [ ] Can approve payment
- [ ] Can execute payment
- [ ] Can complete project
- [ ] Role-based access works
- [ ] MetaMask interactions work
- [ ] UI updates after transactions

---

## 🐛 If Tests Fail

1. **Check Hardhat node is running:**
   ```bash
   npm run node
   ```

2. **Check contract is deployed:**
   ```bash
   npx hardhat run scripts/check-admin.js --network localhost
   ```

3. **Redeploy if needed:**
   ```bash
   npm run deploy:local
   ```

4. **Refresh browser after redeployment**

---

## ✅ Success Criteria

Your DApp is working if:
- ✅ Automated script completes all 10 tests
- ✅ Can create and manage projects in UI
- ✅ Can perform payment workflow
- ✅ All roles work correctly
- ✅ No console errors

---

## 🎉 Next Steps

Once all tests pass:
1. Remove the debug box from `App.js`
2. Test edge cases
3. Deploy to Sepolia testnet
4. Share with team for feedback

---

**Start with the automated test, then do a quick manual test in the browser!** 🚀
