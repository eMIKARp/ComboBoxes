# ComboBoxes
a piece of code that displays a frame with combobox on it which changes its backgroud color 

    package listykombinowane;

    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;
    

    public class Main 
    {     
    
    private JFrame oknoGlowne = new JFrame();
    private JPanel panelGlowny = new JPanel();
    private JComboBox cBox = new JComboBox();
    
    public Main()
    {
       initComponents(); 
    }
    
    public void initComponents()
    {
        oknoGlowne.getContentPane().add(panelGlowny);
        panelGlowny.add(cBox);
        
        oknoGlowne.setTitle("Listy kombinowane");
        oknoGlowne.setBounds(300,300,300,200);
        oknoGlowne.setVisible(true);
        
        oknoGlowne.setDefaultCloseOperation(3);
        
        cBox.addItem(new ColorHandler(Color.RED, "Czerwony"));
        cBox.addItem(new ColorHandler(Color.YELLOW, "Żółty"));
        cBox.addItem(new ColorHandler(Color.GREEN, "Zielony"));
        
        cBox.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) 
            {
                ColorHandler handler = (ColorHandler)((JComboBox)e.getSource()).getSelectedItem();
                ((JComboBox)e.getSource()).setBackground(handler.getColor());
            }
        });
       
    private class ColorHandler
    {
        public ColorHandler(Color color, String colorName)
        {
            this.color = color;
            this.colorName = colorName;
        }
        
        @Override
        public String toString()
        {
            return this.colorName;
        }
        
        public Color getColor()
        {
            return this.color;
        }
        
        private Color color;
        private String colorName;
    }
        
    }
    public static void main(String[] args) {
        new Main();
    }
    
    }
