import javax.swing.JOptionPane;

public class ATMSystem {

    public int chooseAccount(int accountsCreated) {
        String menu = "Choose Account:\n";

        for (int i = 0; i < accountsCreated; i++) {
            menu += "[" + (i + 1) + "] Account " + (i + 1) + "\n";
        }

        String choice = JOptionPane.showInputDialog(menu);
        if (choice == null) return -1;

        try {
            int num = Integer.parseInt(choice);
            if (num >= 1 && num <= accountsCreated) return num - 1;

        } catch (Exception e) {}
        invalidOption();
        return -1;
    }

    public int chooseSpecificAccount(String message) {
        String choice = JOptionPane.showInputDialog(
                message + "\n[1] Account 1\n[2] Account 2");

        if (choice == null) return -1;

        try {
            int num = Integer.parseInt(choice);
            if (num == 1 || num == 2) return num - 1;
        } catch (Exception e) {}

        invalidOption();
        return -1;
    }

    public void showDetails(String name, double balance) {
        JOptionPane.showMessageDialog(null,
                "=== ACCOUNT DETAILS ===\n" +
                "Account Name: " + name + "\n" +
                String.format("Current Balance: ₱%.2f", balance));
    }

    public void showAllAccounts(String[] names, double[] balances, int count) {
        StringBuilder sb = new StringBuilder("=== ALL ACCOUNTS ===\n\n");

        for (int i = 0; i < count; i++) {
            sb.append("Account ").append(i + 1).append(":\n")
              .append("Name: ").append(names[i]).append("\n")
              .append(String.format("Balance: ₱%.2f\n\n", balances[i]));
        }

        JOptionPane.showMessageDialog(null, sb.toString());
    }

    public void depositSuccess() { JOptionPane.showMessageDialog(null, "Successfully deposited!"); }
    public void withdrawSuccess() { JOptionPane.showMessageDialog(null, "Successfully withdrawn!"); }

    public void transferSuccess(String from, String to, double amount) {
        JOptionPane.showMessageDialog(null,
                "Transfer Successful!\n\n₱" + amount +
                " transferred from:\n" + from + "\n→ " + to);
    }

    public void invalidAmount() { JOptionPane.showMessageDialog(null, "Invalid amount!"); }
    public void insufficientFunds() { JOptionPane.showMessageDialog(null, "Insufficient funds!"); }
    public void invalidOption() { JOptionPane.showMessageDialog(null, "Invalid option. Try again!"); }
    public void exitMessage() { JOptionPane.showMessageDialog(null, "Exiting... Thank you!"); }


    public boolean isDivisibleBy100(double amount) {
        return amount % 100 == 0;
    }

    public void notDivisibleBy100() {
        JOptionPane.showMessageDialog(null,
                "Amount must be divisible by 100!");
    }


    public boolean isWithinLimits(double amount) {
        return amount >= 2000 && amount <= 100000;
    }

    public void amountOutOfRange() {
        JOptionPane.showMessageDialog(null,
                "Amount must be AT LEAST ₱2,000 and NOT MORE than ₱100,000!");
    }
}
