# Lab-Report04
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.Random;

public class DrawCircle extends JFrame implements ActionListener {

    private JButton drawButton;
    private JButton clearButton;
    private DrawPanel panel;
    private int x = -1, y = -1;
    private final int DIAMETER = 60;

    public DrawCircle() {
        setTitle("Draw Circle Application");
        setSize(500, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        drawButton = new JButton("Draw Circle");
        clearButton = new JButton("Clear");

        drawButton.addActionListener(this);
        clearButton.addActionListener(this);

        JPanel buttonPanel = new JPanel();
        buttonPanel.add(drawButton);
        buttonPanel.add(clearButton);

        panel = new DrawPanel();

        add(buttonPanel, BorderLayout.NORTH);
        add(panel, BorderLayout.CENTER);

        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == drawButton) {
            Random rand = new Random();
            x = rand.nextInt(panel.getWidth() - DIAMETER);
            y = rand.nextInt(panel.getHeight() - DIAMETER);
        } else if (e.getSource() == clearButton) {
            x = -1;
            y = -1;
        }
        panel.repaint();
    }

    class DrawPanel extends JPanel {
        @Override
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            if (x != -1 && y != -1) {
                g.setColor(Color.BLUE);
                g.fillOval(x, y, DIAMETER, DIAMETER);
            }
        }
    }

    public static void main(String[] args) {
        new DrawCircle();
    }
}
```
