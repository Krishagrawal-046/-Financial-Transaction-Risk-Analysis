**Financial Transaction Risk Analysis with SQL**
    This repository contains an SQL-based project for detecting fraud and money laundering risks in financial transactions. Using a dataset of simulated transactions, we apply analytical queries to uncover patterns like balance inconsistencies, mule accounts, large suspicious transfers, and complex laundering schemes. The project is designed to highlight how SQL can support risk mitigation in banking and finance.
    The analysis focuses on:
    -> Summarizing transaction patterns and volumes.
    -> Identifying inconsistencies in account balances post-transaction.
    -> Flagging potential mule accounts with repeated zero balances.
    -> Detecting high-risk activities such as large transfers, high-frequency operations, and circular money flows.

**Dataset Overview**
    The dataset (transactions.csv) includes over 20,000 transaction records, covering types like PAYMENT, TRANSFER, CASH_OUT, and DEPOSIT. It simulates real-world financial data with balance updates for senders and recipients.
    **Table Name:** transactions
    **Columns:**
        transaction_id (INT): Unique identifier for each transaction.
        step (INT): Time step (e.g., representing hours or days).
        transaction_type (VARCHAR): Type of transaction (e.g., 'TRANSFER', 'CASH_OUT').
        amount (DECIMAL): Transaction amount.
        sender_account (VARCHAR): Sender's account ID.
        sender_old_balance (DECIMAL): Sender's balance before the transaction.
        sender_new_balance (DECIMAL): Sender's balance after the transaction.
        recipient_account (VARCHAR): Recipient's account ID (or merchant ID for PAYMENTS).
        recipient_old_balance (DECIMAL): Recipient's balance before the transaction.
        recipient_new_balance (DECIMAL): Recipient's balance after the transaction.
        is_suspicious (INT): Flag indicating if the transaction is marked as suspicious (1 = yes, 0 = no).

**Key Analytical Queries**
    The project includes 15 SQL queries stored in Financial Transaction Risk- REPORT QUERY DOCUMENT.pdf. Here's a summary of the main ones:

    1) Transaction Summary: Counts total transactions, calculates average and max amounts.
    2) Top Largest Transactions: Lists the 10 highest-value transactions with details.
    3) Balance Mismatches: Finds transactions where balances don't update as expected (e.g., old - amount ≠ new).
    4) Zero-Balance Mule Accounts: Identifies recipients with frequent zero balances (potential fraud conduits).
    5) Large Transfers/Cash-Outs: Filters transfers or cash-outs exceeding $200,000.
    6) High-Frequency Transfers: Detects accounts making multiple transfers in the same time step (structuring indicator).
    7) Round-Trip Laundering: Spots pairs of accounts exchanging funds back and forth.
    8) Structuring Patterns: Flags senders distributing identical amounts to multiple recipients.
    9) Collector Accounts (Top 10): Recipients receiving from many unique senders.
    10) Distributor Accounts (Top 10): Senders transferring to many unique recipients.
    11) Chain Laundering: Tracks multi-step flows (e.g., A → B → C) in the same step.
    12) Mule-Related Transactions: All activity involving flagged mule accounts.
    13) Volume by Transaction Type: Aggregates counts and totals per type.
    14) Daily Suspicious Amounts: Sums risky amounts per step (e.g., large or mule-involved).
    15) Dual-Role Accounts: Accounts that both send and receive, often intermediaries in laundering.

These queries use aggregations (COUNT, SUM, AVG), joins for pattern detection, and filters for risk flagging.
