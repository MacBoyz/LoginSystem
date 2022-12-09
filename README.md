# LoginSystem
First Repository
import java.awt.Color;
import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.*;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPasswordField;
import javax.swing.JTextField;

public class LoginPage implements ActionListener {
	JFrame frame = new JFrame();
	JButton login = new JButton("Login");
	JButton reset = new JButton("Reset");
	JTextField userID = new JTextField();
	JPasswordField password = new JPasswordField();
	JLabel userId = new JLabel("UserId:");
	JLabel userpassword = new JLabel("Password:");
	JLabel message = new JLabel();
	HashMap<String, String> log = new HashMap<String, String>();

	LoginPage(HashMap<String, String> logOriginal) {
		log = logOriginal;
		userId.setBounds(70, 120, 50, 30);
		userpassword.setBounds(70, 150, 75, 30);
		userID.setBounds(130, 125, 200, 25);
		password.setBounds(130, 150, 200, 25);

		login.setBounds(125, 200, 100, 25);
		login.addActionListener(this);

		reset.setBounds(225, 200, 100, 25);
		reset.addActionListener(this);

		frame.add(userId);
		frame.add(userpassword);
		frame.add(message);
		frame.add(userID);
		frame.add(password);
		frame.add(login);
		frame.add(reset);

		message.setBounds(130, 240, 240, 40);
		message.setFont(new Font(null, Font.ITALIC, 25));
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setSize(500, 500);
		frame.setLayout(null);
		frame.setVisible(true);
	}

	public void actionPerformed(ActionEvent e) {
		if (e.getSource() == reset) {
			userID.setText("");
			password.setText("");
		}
		if (e.getSource() == login) {
			String userIDField = userID.getText();
			String Password = String.valueOf(password.getPassword());
			if (log.containsKey(userIDField)) {
				if (log.get(userIDField).equals(Password)) {
					message.setForeground(Color.blue);
					message.setText("Login succesful");
				} else {
					message.setForeground(Color.green);
					message.setText("Wrong Password");
				}
			} else {
				message.setForeground(Color.red);
				message.setText("User Not Found");
			}
		}
	}
}
