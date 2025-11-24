Here is the essential documentation and a solid starting plan to set up bookkeeping for your LLC using GnuCash, based on the official guides and community wisdom.

### 📚 Core Documentation & Key Concepts

To build a strong foundation, start with these official resources that explain both the "how" and the "why" of double-entry accounting in GnuCash.

| Resource | Description | Key Takeaways |
| :--- | :--- | :--- |
| **GnuCash Documentation Portal** | Central hub for all guides/manuals. | Access the *Tutorial and Concepts Guide* (learning) and the *GnuCash Manual* (reference). |
| **Tutorial and Concepts Guide** | Primary guide for learning GnuCash. | Explains the 5 basic account types (Assets, Liabilities, Equity, Income, Expenses) and double-entry principle. |
| **Quick Start Guide for Business Users** | Wiki page with business-specific advice. | GnuCash is single-user; use separate files for business/personal accounting; create a "sandbox" for practice. |

### 💼 Business Setup Workflow

Once you understand the basics, follow this workflow to configure GnuCash for your LLC.

- **Install GnuCash on Debian**
    - **Via APT**: The simplest method is `sudo apt install gnucash`.
    - **Via Flatpak**: For a more recent version, use Flatpak. First, set it up with `sudo apt install flatpak && flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`, then install with `flatpak install flathub org.gnucash.GnuCash`.

- **Create Your Business Chart of Accounts**
    - **Use the Business Template**: When creating a new file via `File → New File`, the setup assistant will ask you to "Choose Accounts to Create." **Deselect "Common Accounts" and select "Business Accounts" instead** to get a pre-configured hierarchy for businesses.
    - **Core Accounts for an LLC**: The template will provide a good starting structure. Ensure you have these key account types:
        - **Assets**: `Accounts Receivable` (A/Receivable type), `Checking Account` (Bank type).
        - **Liabilities**: `Accounts Payable` (A/Payable type), `Tax` (Liability type) with sub-accounts for `Tax on Sales` and `Tax on Purchases`.
        - **Income**: `Sales`.
        - **Expenses**: Create sub-accounts for your business expenses (e.g., `Office Supplies`, `Rent`).

- **Configure Sales Tax**
    - Navigate to `Business → Tax Tables` to set up your sales tax rates.
    - For each tax (e.g., state, county), create an entry with a **Name**, **Type** (Percent), **Value** (the percentage), and **Account** (pointing to your `Liabilities:Tax on Sales` account).

- **Enter Your Company Information**
    - Go to `Edit → Book Options` and click the **Business** tab. Enter your LLC's name, contact information, and select your default tax tables for customers and vendors.

### 🚀 A Practical First-Use Plan

- **Start with a Sandbox**: Before touching your real books, create a separate practice file to experiment with creating accounts, entering invoices, and generating reports.
- **Enter Opening Balances**: When you start, you will need to record the current balances of your LLC's bank accounts. This is typically done by creating a transaction that transfers money from an "Opening Balances" equity account to your asset account (e.g., Checking).
- **Stick to the Workflow**: For invoicing customers, always use `Business → Customer → Enter Invoice` and then `Post Invoice`. For paying bills, use `Business → Vendor → Enter Bill` and then `Post Bill`. **Do not** manually add transactions to Accounts Receivable or Payable accounts.
- **Run Key Reports**: After entering data, use `Reports → Business` to generate essential reports like **Accounts Receivable** and **Profit & Loss**.

GnuCash is a powerful tool that can handle your LLC's bookkeeping needs. The key is starting with the provided business template and adhering to the double-entry accounting process.

If you run into specific questions while setting up your chart of accounts or entering your first invoices, feel free to ask.
