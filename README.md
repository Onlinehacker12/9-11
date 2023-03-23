# 9-11
Airplane game
import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class AirplaneGame extends JPanel implements KeyListener {
    private int x = 50; // airplane's x position
    private int y = 200; // airplane's y position
    private int dx = 0; // airplane's x speed
    private int dy = 0; // airplane's y speed

    public AirplaneGame() {
        JFrame frame = new JFrame("Airplane Game");
        frame.add(this);
        frame.setSize(500, 500);
        frame.setVisible(true);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.addKeyListener(this);
    }

    public void paint(Graphics g) {
        // Draw the airplane
        g.setColor(Color.RED);
        g.fillRect(x, y, 30, 10);

        // Draw the Washington Monument
        g.setColor(Color.BLACK);
        g.fillRect(200, 100, 20, 300);

        // Draw the Capitol Building
        g.setColor(Color.BLUE);
        g.fillRect(300, 150, 100, 100);
    }

    public void keyPressed(KeyEvent e) {
        // Move the airplane based on the arrow keys
        if (e.getKeyCode() == KeyEvent.VK_LEFT) {
            dx = -5;
        } else if (e.getKeyCode() == KeyEvent.VK_RIGHT) {
            dx = 5;
        } else if (e.getKeyCode() == KeyEvent.VK_UP) {
            dy = -5;
        } else if (e.getKeyCode() == KeyEvent.VK_DOWN) {
            dy = 5;
        }
    }

    public void keyReleased(KeyEvent e) {
        // Stop moving the airplane when the arrow keys are released
        if (e.getKeyCode() == KeyEvent.VK_LEFT || e.getKeyCode() == KeyEvent.VK_RIGHT) {
            dx = 0;
        } else if (e.getKeyCode() == KeyEvent.VK_UP || e.getKeyCode() == KeyEvent.VK_DOWN) {
            dy = 0;
        }
    }

    public void keyTyped(KeyEvent e) {}

    public void moveAirplane() {
        // Move the airplane
        x += dx;
        y += dy;

        // Repaint the screen
        repaint();
    }

    public static void main(String[] args) throws InterruptedException {
        AirplaneGame game = new AirplaneGame();

        while (true) {
            game.moveAirplane();
            Thread.sleep(10);
        }
    }
}
