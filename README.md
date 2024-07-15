using System;
using System.Drawing;
using System.Windows.Forms;

public class AppleForm : Form
{
    public AppleForm()
    {
        this.Text = "Apple Drawing";
        this.Paint += new PaintEventHandler(DrawApple);
        this.Width = 400;
        this.Height = 400;
    }

    private void DrawApple(object sender, PaintEventArgs e)
    {
        Graphics g = e.Graphics;

        // Draw the apple body
        Brush appleBrush = new SolidBrush(Color.Red);
        g.FillEllipse(appleBrush, 100, 100, 200, 200);

        // Draw the apple stem
        Pen stemPen = new Pen(Color.Brown, 5);
        g.DrawLine(stemPen, 200, 70, 200, 130);

        // Draw a leaf
        Brush leafBrush = new SolidBrush(Color.Green);
        Point[] leafPoints = { new Point(200, 70), new Point(230, 40), new Point(210, 70) };
        g.FillPolygon(leafBrush, leafPoints);
    }

    [STAThread]
    public static void Main()
    {
        Application.Run(new AppleForm());
    }
}
