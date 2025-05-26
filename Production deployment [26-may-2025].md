### sheba-pay-integration-partner

- Migrations
  
**TAG : 3**

- Change the transactionType column of the active_partner_gateways table from ENUM to String.
  
---

### sheba-pay-add-money-integration

- env
  
```env
SPAY_BASE_URL=https://middleware.dev-sheba.xyz/spayapi
PAYMENT_KEYWORD=PMNT
```

**TAG : 6**

- Rename PADDM to ADDM
- Use a different integration wallet for pass-through transactions.
- Implement AML API for pass-through.

