#ใบงานที่ 11
##การเขียนโปรแกรมกราฟฟิกส์ด้วย GDI+ (3)
## กล่าวนำ
ใบงานนี้ มีวัตถุประสงค์ เพื่อให้นักศึกษา ได้รู้จักกับ GDI+ ซึ่งจะช่วยให้นักษาสามารถ

* วาดรูปร่างต่างๆ โดยใช้ GDI+ ได้

## การใช้งานแปรงระบายสี (Brush)
แปรงระบายสี ช่วยให้เราสามารถระบายสีแบบต่างๆ ให้กับรูปร่างต่างๆ ได้ตามต้องการ ใน GDI+ มีแปรงระบายสีอยู่ 5 รูปแบบด้วยกัน ประกอบด้วย ```SolidBrush```, ```HatchBrush```, ```TextureBrush```, ```LinearGradientBrush``` และ ```PathGradientBrush``` ซึ่งทั้งหมดจะอยู่ในคลาส ```Brush``` 

### การระบายสีด้วย SolidBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-1.png">
</p>

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/1.JPG)

### การระบายสีด้วย HatchBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
 <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-2.png">
</p>

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/2.JPG)

### การระบายสีด้วย TextureBrush
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void Form1_Paint(object sender, PaintEventArgs e)```
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-3.png">
</p>
**หมายเหตุ** ชื่อรูปในบรรทัดที่ 22 ให้เปลี่ยนเป็นที่ตั้งจริงของรูปที่นักศึกษาใช้

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/3.JPG)


### การระบายสีด้วย TextureBrush
* ให้วางคอนโทรล Panel จำนวน 2 ตัวลงบน Form โดยมีชื่อว่า panel1 และ panel2 ตามลำดับ
 * เพิ่ม paint event ให้กับ panel ทั้งสองตัว
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-4.png">
</p>
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen1_Paint(object sender, PaintEventArgs e)```
  <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-5.png">
</p> 

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/4.JPG)

* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen2_Paint(object sender, PaintEventArgs e)```
   <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-6.png">
</p>

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/5.JPG)

### การระบายสีด้วย Path Gradient Brush

การระบายสีด้วย Path Gradient Brush เป็นการไล่เฉดสีตาม path ที่กำหนด ในโปรแกรมตัวอย่างนี้จะวาดวงรีและไล่เฉดสีจากด้านในออกสู่ด้านนอก
* การทดลอง 
 * ให้ลดขนาด panel1 และ panel2 ลง แล้วเพิ่ม panel3 เข้าไปใน form1 ดังรูป
    <p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-7.png">
</p>

 * เพิ่ม Paint event ให้กับ Panel3
* แก้ไข code ต่อไปนี้ในฟังก์ชัน ```private void palen3_Paint(object sender, PaintEventArgs e)```
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-8.png">
</p>

ผลลัพธ์

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/6.JPG)

###แบบทดสอบ 
ให้เลื่อนจุดศูนย์กลางและปรับเปลี่ยนสี ให้ได้รูปดังนี้
<p align = "center">
<img src= "https://github.com/Desktop-Programming-Lab-2559/LAB-11/blob/master/imgs/lab11-9.png">
</p>

![](https://github.com/fernkamon/LAB-11/blob/master/imgs/7.JPG)
 
 Code
 
 ```
 using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing.Drawing2D;
namespace LAB11_1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

       
        private void panel3_Paint(object sender, PaintEventArgs e)
        {
            GraphicsPath path = new GraphicsPath();
            path.AddEllipse(panel3.ClientRectangle);
            PathGradientBrush br = new PathGradientBrush(path);
            br.CenterPoint = new PointF(panel3.ClientRectangle.Width / 1,
                panel3.ClientRectangle.Height / 10);
            br.CenterColor = Color.White;
            br.SurroundColors = new Color[] { Color.Black };
            e.Graphics.FillPath(br, path);
        }
    }
}

 ```

