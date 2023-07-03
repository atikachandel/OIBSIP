import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class GuessTheNumber extends JFrame {
    private int randomNumber;
    private int attempts;
    private int maxAttempts;
    private JLabel attemptsLabel;
    private JTextField guessTextField;
    private JTextArea outputTextArea;

    public GuessTheNumber(int maxAttempts) {
        this.maxAttempts = maxAttempts;
        this.attempts = 0;

        setTitle("Guess the Number");
        setSize(600, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setLayout(new BorderLayout());

        JPanel topPanel = new JPanel();
        topPanel.setLayout(new FlowLayout());
        JLabel guessLabel = new JLabel("Enter your guess (1-100): ");
        guessTextField = new JTextField(10);
        JButton guessButton = new JButton("Guess");
        guessButton.addActionListener(new GuessButtonListener());
        topPanel.add(guessLabel);
        topPanel.add(guessTextField);
        topPanel.add(guessButton);

        JPanel bottomPanel = new JPanel();
        bottomPanel.setLayout(new FlowLayout());
        attemptsLabel = new JLabel("Attempts: " + attempts + "/" + maxAttempts);
        outputTextArea = new JTextArea(10, 20);
        outputTextArea.setEditable(false);
        bottomPanel.add(attemptsLabel);
        bottomPanel.add(outputTextArea);

        add(topPanel, BorderLayout.NORTH);
        add(bottomPanel, BorderLayout.CENTER);

        generateRandomNumber();
    }

    private void generateRandomNumber() {
        randomNumber = (int) (Math.random() * 100 + 1);
    }

    private class GuessButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            if (attempts >= maxAttempts) {
                JOptionPane.showMessageDialog(GuessTheNumber.this,
                        "You have reached the maximum number of attempts!",
                        "Game Over",
                        JOptionPane.INFORMATION_MESSAGE);
                System.exit(0);
            }

            String guessText = guessTextField.getText();
            try {
                int guess = Integer.parseInt(guessText);
                attempts++;

                if (guess == randomNumber) {
                    outputTextArea.append("Congratulations! You guessed the number in " + attempts + " attempts!\n");
                    guessTextField.setEditable(false);
                } else if (guess < randomNumber) {
                    outputTextArea.append("Higher!\n");
                } else {
                    outputTextArea.append("Lower!\n");
                }

                attemptsLabel.setText("Attempts: " + attempts + "/" + maxAttempts);
                guessTextField.setText("");
                guessTextField.requestFocus();

            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(GuessTheNumber.this,
                        "Invalid input! Please enter a valid number.",
                        "Error",
                        JOptionPane.ERROR_MESSAGE);
            }
        }
    }

    public static void main(String[] args) {
        int maxAttempts = 5;
        SwingUtilities.invokeLater(() -> {
            GuessTheNumber game = new GuessTheNumber(maxAttempts);
            game.setVisible(true);
        });
    }
}
