# Banking Application Use Case Diagram

```mermaid
graph TB
    subgraph "Banking System"
        subgraph "Customer"
            C[Customer]
        end
        
        subgraph "Use Cases"
            UC1[Register Account]
            UC2[Login to Account]
            UC3[View Account Details]
            UC4[Check Balance]
            UC5[Deposit Money]
            UC6[Withdraw Money]
            UC7[Transfer Funds]
            UC8[View Mini Statement]
            UC9[Validate Biometric]
        end
        
        subgraph "System"
            S[Banking System]
        end
    end
    
    %% Customer associations
    C --> UC1
    C --> UC2
    C --> UC3
    C --> UC4
    C --> UC5
    C --> UC6
    C --> UC7
    C --> UC8
    
    %% Include relationships (biometric validation)
    UC6 -.->|<<include>> UC9
    UC7 -.->|<<include>> UC9
    UC8 -.->|<<include>> UC9
    
    %% Extend relationships
    UC2 -.->|<<extend>> UC9
    
    %% System boundary
    classDef customer fill:#e1f5fe
    classDef useCase fill:#f3e5f5
    classDef system fill:#e8f5e8
    
    class C customer
    class UC1,UC2,UC3,UC4,UC5,UC6,UC7,UC8,UC9 useCase
    class S system
```

## Use Case Descriptions:

### Primary Use Cases:
1. **Register Account**: New customer registers with bank account details and biometric
2. **Login to Account**: Customer logs in using account number and biometric authentication
3. **View Account Details**: Customer views details of their linked bank accounts
4. **Check Balance**: Customer inquires about the current balance of a selected account
5. **Deposit Money**: Customer deposits funds into a selected account
6. **Withdraw Money**: Customer withdraws funds from a selected account (requires biometric permission)
7. **Transfer Funds**: Customer transfers money to another account (requires biometric permission)
8. **View Mini Statement**: Customer views recent transactions for a selected account (requires biometric permission)

### Supporting Use Cases:
9. **Validate Biometric**: System validates user's fingerprint (included in sensitive transactions)

### Relationships:
- **Include**: Withdraw Money, Transfer Funds, and View Mini Statement include Validate Biometric
- **Extend**: Login to Account extends Validate Biometric for authentication 