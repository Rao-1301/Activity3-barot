# Activity 3
Name: Barot Pranav
Student ID: 16373096

# Token Address: 0x8464135c8f25da09e49bc8782676a84730c318bc
<img width="1067" height="336" alt="image" src="https://github.com/user-attachments/assets/60c52a49-28d9-4b4d-81e9-81839430b589" />
deploy block 1n

<img width="930" height="250" alt="image" src="https://github.com/user-attachments/assets/0c3b9d59-534f-461a-a004-405ac5b1102d" />

<img width="1046" height="300" alt="image" src="https://github.com/user-attachments/assets/30fa52f0-af8b-492d-8137-9f0c7bb0c90e" />

# Console Output 
<img width="941" height="258" alt="image" src="https://github.com/user-attachments/assets/05c3bfef-4ec9-48ef-88eb-4c9a118ffb1a" />
From contract events & constructor:

Roles granted at deploy:

DEFAULT_ADMIN_ROLE → Admin

MINTER_ROLE → Minter

PAUSER_ROLE → Pauser
<img width="995" height="685" alt="image" src="https://github.com/user-attachments/assets/9f5971a1-7ed6-45f7-aa27-c7d1e18c3a32" />
<img width="1144" height="221" alt="image" src="https://github.com/user-attachments/assets/e1f9a9c6-2d2a-4e8f-840e-8c8484dee8fc" />

# Short note on gas Awareness
Our batch airdrop is gas-aware because it executes multiple token transfers in a single transaction rather than sending them individually. This design amortizes the gas cost across all recipients, reducing overhead.

Key gas-saving features:
Custom Errors – The contract uses ArrayLengthMismatch and CapExceeded errors instead of require() strings, which are cheaper in gas when reverting.
Calldata Usage – Recipients and amounts are passed as calldata arrays, minimizing memory copying and lowering gas.
Unchecked Loops – The for loops use unchecked { ++i; } to skip redundant overflow checks, saving gas on iteration.
Single Transaction Amortization – Instead of multiple transfer() calls, minting to all recipients at once reduces total gas by ~25.65% as shown in our output:

Batch gasUsed: 77899
Singles total gasUsed: 104780
Singles total gasUsed: 104780
This demonstrates that batching transactions in a smart contract is significantly more efficient than sending individual transfers.
