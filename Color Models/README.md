### Description:
<br>
The challenge is to write an application to convert colors from one model to another. The application supports the following color models: RGB, LAB, XYZ, HSV, HSL, CMYK. The application also warns the user about the possibility of color loss during some translations from one color model to another. To implement the application, a programming language С# and framework WPF were chosen.The application works according to the principle of converting all color models to RGB, and then to the one that is needed if the RGB system is not required
<br>
### Code examples:
<br>
Method to convert from XYZ system to RGB:
<br>

``` cs
private System.Windows.Media.Color XyzToRgb(string[] mas)
{
    ColorHelper.XYZ xyz = new ColorHelper.XYZ(int.Parse(mas[0]), 
    int.Parse(mas[1]), int.Parse(mas[2]));
    ColorHelper.RGB rgb = ColorHelper.ColorConverter.XyzToRgb(xyz);
    System.Windows.Media.Color color = new System.Windows.Media.Color();
    color.R = rgb.R;
    color.G = rgb.G;
    color.B = rgb.B;
    return color;
}
```
<br>
Method to convert from  LAB system to RGB:
<br>

```cs
private System.Windows.Media.Color LabToRgb(string[] mas)
{
    double L = double.Parse(mas[0]);
    double A = double.Parse(mas[1]);
    double B = double.Parse(mas[2])
    double X, Y, Z, x, y, z, f_x, f_y, f_z
    f_y = (L + 16.0) / 116.0;
    f_x = (A / 500.0) + f_y;
    f_z = f_y - (B / 200.0)
    if (Math.Pow(f_x, 3) > 0.008856)
    {
        x = Math.Pow(f_x, 3);
    }
    else
    {
        x = ((116.0 * f_x) - 16.0) / 903.3;
    
    if (L > 903.3 * 0.008856)
    {
        y = Math.Pow(((L + 16.0) / 116.0), 3);
    }
    else
    {
        y = L / 903.3;
    
    if (Math.Pow(f_z, 3) > 0.008856)
    {
        z = Math.Pow(f_z, 3);
    }
    else
    {
        z = ((116.0 * f_z) - 16.0) / 903.3;
    
    X = x * 95.047;
    Y = y * 100.0;
    Z = z * 108.883
    XYZ xyz = new XYZ(X, Y, Z);
    RGB rgb = ColorHelper.ColorConverter.XyzToRgb(xyz)
    System.Windows.Media.Color color = new System.Windows.Media.Color();
    color.R = rgb.R;
    color.G = rgb.G;
    color.B = rgb.B;
    return color
}
```