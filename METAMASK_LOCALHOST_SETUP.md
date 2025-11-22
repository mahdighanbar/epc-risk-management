# MetaMask Localhost Setup Guide

## Add Localhost Network to MetaMask

### Step-by-Step Instructions:

1. **Open MetaMask extension**

2. **Click the network dropdown** at the top
   - It currently shows "Sepolia" or another network name
   - Click on it to open the network list

3. **Scroll down and click "Add network"**

4. **Click "Add a network manually"** (at the bottom)

5. **Fill in these exact details:**

   ```
   Network name: Localhost 8545
   New RPC URL: http://127.0.0.1:8545
   Chain ID: 31337
   Currency symbol: ETH
   ```

6. **Click "Save"**

7. **MetaMask will automatically switch to this network**

8. **Refresh your website** (press F5)

## Verify It Worked

After switching, your debug box should show:
- Chain ID: **31337** ✅ (not 11155111)
- User Role: **admin** ✅ (not user)

## Screenshots of Values

### Network Details to Enter:
```
Network name:        Localhost 8545
New RPC URL:         http://127.0.0.1:8545
Chain ID:            31337
Currency symbol:     ETH
Block explorer URL:  (leave empty)
```

## Common Issues

### "Invalid Chain ID" error
- Make sure you typed exactly: `31337` (no spaces)

### "RPC URL already in use"
- The network might already exist, look for "Localhost 8545" in your network list

### Still showing wrong Chain ID after refresh
- Make sure MetaMask actually switched (check the network name at top of MetaMask)
- Try disconnecting and reconnecting your wallet on the website

## Quick Test

After setup, go to your website and check:
- Debug box shows Chain ID: 31337 ✅
- Debug box shows User Role: admin ✅
- You can see "Create Project" button on Projects page ✅
