# Act.11CJ
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Triangulo triangulo = new Triangulo();
        Circulo circulo = new Circulo();
        Cuadrado cuadrado = new Cuadrado();
        double entrada;
        boolean flag = false;

        do {
            System.out.println("Selecciona la figura que quieres: \n1.Circulo \n2.Triangulo \n3.Cuadrado \n");
            entrada = Double.valueOf(scanner.nextLine());
            switch ((int) entrada) {
                case 1:
                    System.out.println("Ingrese el Diametro: ");
                    entrada = Double.valueOf(scanner.nextLine());
                    circulo.setDiametro(entrada);
                    System.out.println("Elije el valor a obtener: \n1.Area\n2.Perimetro ");
                    entrada = Double.valueOf(scanner.nextLine());
                    if (entrada == 1) System.out.println("El area es: " + circulo.getArea());
                    else if (entrada == 2) System.out.println("El perimetro es: " + circulo.getPerimetro());

                case 2:
                    System.out.println("Ingrese la base: ");
                    entrada = Double.valueOf(scanner.nextLine());
                    triangulo.setBase(entrada);
                    System.out.println("Ingrese la altura: ");
                    entrada = Double.valueOf(scanner.nextLine());
                    triangulo.setAltura(entrada);
                    System.out.println("Elije el valor a obtener: \n1.Area\n2.Perimetro ");
                    entrada = Double.valueOf(scanner.nextLine());
                    if (entrada == 1) System.out.println(" El area es: " + triangulo.getArea());
                    else if (entrada == 2) System.out.println("El perimetro es: " + triangulo.getPerimetro());

                case 3:
                    System.out.println("Ingrese el tamano del lado: ");
                    entrada = Double.valueOf(scanner.nextLine());
                    cuadrado.setLado(entrada);
                    System.out.println("Seleccione el valor a obtener: \n1.Area\n2.Perimetro ");
                    entrada = Double.valueOf(scanner.nextLine());
                    if (entrada == 1) System.out.println(" El area es: " + cuadrado.getArea());
                    else if (entrada == 2) System.out.println("El perimetro es: " + cuadrado.getPerimetro());

            }
        } while (flag != true);
    }
----------------

public class Circulo implements Shape{
    private double diametro;

    @Override
    public double getArea(){
        return ((diametro/2)*(diametro/2)) * 3.1416;
    }

    @Override
    public double getPerimetro(){
        return 2 * 3.1416 * (diametro/2);
    }

    public double getDiametro(){
        return diametro;
    }

    public void setDiametro(double diametro){
        this.diametro = diametro;
    }
}
----------------

public class Triangulo implements Shape{

    private double base;
    private double altura;

    @Override
    public double getArea(){
        return (base * altura)/2;
    }

    @Override
    public double getPerimetro(){
        return base + altura + getHipotenusa();
    }

    public double getHipotenusa(){
        return Math.sqrt(Math.pow(base, 2) + Math.pow(altura, 2));
    }

    public double getBase(){
        return base;
    }

    public void setBase(double base){
        this.base = base;
    }

    public double getAltura(){
        return altura;
    }

    public void setAltura(double altura){
        this.base = base;
    }
}
-----------------

public class Cuadrado implements Shape{
    private double lado;

    @Override
    public double getArea(){
        return lado * lado;
    }

    @Override
    public double getPerimetro(){
        return lado * 4;
    }

    public double getLado(){
        return lado;
    }

    public void setLado(double lado){
        this.lado = lado;
    }
}
-------------------

public interface Shape {
    double getArea();
    double getPerimetro();
}
