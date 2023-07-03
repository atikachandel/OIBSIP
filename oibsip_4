import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class QuizApp extends JFrame {
    private String username;
    private int timeRemaining;
    private Timer timer;
    private JLabel timerLabel;
    private JButton loginButton;
    private JButton updateProfileButton;
    private JButton startQuizButton;
    private JButton logoutButton;
    private JButton closeSessionButton;
    private JTextArea outputTextArea;

    public QuizApp() {
        setTitle("Quiz Application");
        setSize(600, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setLayout(new BorderLayout());

        JPanel topPanel = new JPanel();
        topPanel.setLayout(new FlowLayout());
        JLabel userLabel = new JLabel("Username:  \n");
        JTextField userTextField = new JTextField(10);
        JLabel passLabel = new JLabel("Password:  \n");
        JPasswordField passField = new JPasswordField(10);
        loginButton = new JButton("\nLogin");
        loginButton.addActionListener(new LoginButtonListener(userTextField, passField));
        topPanel.add(userLabel);
        topPanel.add(userTextField);
        topPanel.add(passLabel);
        topPanel.add(passField);
        topPanel.add(loginButton);

        JPanel centerPanel = new JPanel();
        centerPanel.setLayout(new FlowLayout());
        updateProfileButton = new JButton("Update Profile and Password");
        updateProfileButton.setEnabled(false);
        updateProfileButton.addActionListener(new UpdateProfileButtonListener());
        startQuizButton = new JButton("Start Quiz");
        startQuizButton.setEnabled(false);
        startQuizButton.addActionListener(new StartQuizButtonListener());
        centerPanel.add(updateProfileButton);
        centerPanel.add(startQuizButton);

        JPanel bottomPanel = new JPanel();
        bottomPanel.setLayout(new FlowLayout());
        timerLabel = new JLabel("Timer: 0");
        logoutButton = new JButton("Logout");
        logoutButton.setEnabled(false);
        logoutButton.addActionListener(new LogoutButtonListener());
        closeSessionButton = new JButton("Close Session");
        closeSessionButton.setEnabled(false);
        closeSessionButton.addActionListener(new CloseSessionButtonListener());
        outputTextArea = new JTextArea(10, 30);
        outputTextArea.setEditable(false);
        bottomPanel.add(timerLabel);
        bottomPanel.add(logoutButton);
        bottomPanel.add(closeSessionButton);
        bottomPanel.add(outputTextArea);

        add(topPanel, BorderLayout.NORTH);
        add(centerPanel, BorderLayout.CENTER);
        add(bottomPanel, BorderLayout.SOUTH);

        timeRemaining = 60; // Set the initial time for the quiz
        timer = new Timer(1000, new TimerListener());
    }

    private class LoginButtonListener implements ActionListener {
        private JTextField userTextField;
        private JPasswordField passField;

        public LoginButtonListener(JTextField userTextField, JPasswordField passField) {
            this.userTextField = userTextField;
            this.passField = passField;
        }

        public void actionPerformed(ActionEvent e) {
            username = userTextField.getText();
            String.valueOf(passField.getPassword());

            // Perform authentication (you may use a database or other authentication mechanism here)
            boolean authenticated = true; // Placeholder for authentication, assume always true for the demo

            if (authenticated) {
                updateProfileButton.setEnabled(true);
                startQuizButton.setEnabled(true);
                logoutButton.setEnabled(true);
                closeSessionButton.setEnabled(true);
                loginButton.setEnabled(false);
                outputTextArea.append("Logged in successfully as " + username + "\n");
            } else {
                JOptionPane.showMessageDialog(QuizApp.this,
                        "Invalid username or password!",
                        "Authentication Error",
                        JOptionPane.ERROR_MESSAGE);
            }

            userTextField.setText("");
            passField.setText("");
        }
    }

    private class UpdateProfileButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            // Perform profile and password update
            outputTextArea.append("Updating profile and password for " + username + "\n");
            // Placeholder for the demo
        }
    }

    private class StartQuizButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            outputTextArea.append("Quiz started for " + username + "\n");
            timer.start();
            // Present the MCQ questions and allow user to select answers
            // Placeholder for the demo
        }
    }

    private class LogoutButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            outputTextArea.append("Logged out " + username + "\n");
            username = "";
            updateProfileButton.setEnabled(false);
            startQuizButton.setEnabled(false);
            logoutButton.setEnabled(false);
            closeSessionButton.setEnabled(false);
            loginButton.setEnabled(true);
        }
    }

    private class CloseSessionButtonListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            outputTextArea.append("Session closed for " + username + "\n");
            username = "";
            updateProfileButton.setEnabled(false);
            startQuizButton.setEnabled(false);
            logoutButton.setEnabled(false);
            closeSessionButton.setEnabled(false);
            loginButton.setEnabled(true);
        }
    }

    private class TimerListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            timeRemaining--;
            timerLabel.setText("Timer: " + timeRemaining);

            if (timeRemaining <= 0) {
                timer.stop();
                outputTextArea.append("Time's up! Quiz submitted.\n");
                // Auto submit the quiz
                // Placeholder for the demo
            }
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            QuizApp app = new QuizApp();
            app.setVisible(true);
        });
    }
}
