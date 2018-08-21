freeglut-eclipse-tutorial

### Requisitos

* Eclipse instalado (preferencialmente a versão Photon)
* Compilador MinGW-w64 ([32 bits](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/8.1.0/threads-posix/dwarf/i686-8.1.0-release-posix-dwarf-rt_v6-rev0.7z/download) / [64 bits](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z/download))
* FreeGLUT pré-compilado especificamente para o MinGW ([Link](https://github.com/bnoleto/freeglut-eclipse-tutorial/raw/master/freeglut-MinGW-3.0.0-1.mp.zip)) (por [Transmission Zero](https://www.transmissionzero.co.uk/))

### Passo-a-passo

1. Descompactar o arquivo .7z do MinGW e colocar a pasta principal na raiz do disco rígido (C:\mingw64);

2. Abrir as Variáveis de Ambiente de Sistema e adicionar a pasta “C:\mingw64\bin” à variável PATH;

3. Descompactar o arquivo .zip do FreeGlut e colocar a pasta principal dentro da pasta do mingw64 preferencialmente;

4. Ao criar um novo projeto em C++ no Eclipse, selecione o compilador MinGW, e utilize como base o projeto “Hello World” padrão;

5. Vá até as propriedades do projeto, vá em C/C++ Build > Settings > GCC C++ Compiler > Includes e adicione a pasta “include” do FreeGLUT (C:\mingw64\freeglut\include) na lista de include paths;

6. Ainda nas propriedades da C/C++ Build, vá em MinGW C++ Linker > Libraries e adicione as bibliotecas *opengl32*, *glu32* e *freeglut* na lista de libraries;

7. Adicione a pasta “C:\mingw64\freeglut\lib\x64” do FreeGLUT à library search path na mesma tela. (Caso utilize um sistema de 32 bits, adicione a freeglut/lib/ em vez disso);

8. Copie o arquivo “freeglut.dll” na pasta freeglut/bin/x64 para a C:\Windows\System32 **OU** apenas copie este arquivo para a mesma pasta onde o executável do projeto está localizado (provavelmente dentro de “seu_projeto\Debug\”)

9. Teste seu código e verifique se o programa roda normalmente.

### Hello World utilizando o GLUT
```c++
#include <GL/glut.h>

void display()
{
    glClear(GL_COLOR_BUFFER_BIT);
    glBegin(GL_POLYGON);
        glVertex2f(0.0, 0.0);
        glVertex2f(0.5, 0.0);
        glVertex2f(0.5, 0.5);
        glVertex2f(0.0, 0.5);
    glEnd();
    glFlush();
}

int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_SINGLE);
    glutInitWindowSize(300, 300);
    glutInitWindowPosition(100, 100);
    glutCreateWindow("Olá mundo!");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}
```
