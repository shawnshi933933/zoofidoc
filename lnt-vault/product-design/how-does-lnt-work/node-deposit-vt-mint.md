# Node Deposit/VT Mint

When a user deposits a Node NFT into the LNT Vault, the protocol mints VT based on the aVT parameters.

$$
VT Amount = aVT * (1 -VTC)
$$

Where:

aVT: Accrued Vesting Token. Different projects have distinct methods for calculating aVT.

VTC: Commission collected by LNT

### Workflow:

1 . Validation: The vault verifies the NFT's authenticity and aVT parameters.

2 . Calculation: VT Amount is computed using the above formula.

3 . Minting: VT and YT are issued to the user's wallet.

4 . Escrow: The NFT is securely held in the vault contract until redemption.
