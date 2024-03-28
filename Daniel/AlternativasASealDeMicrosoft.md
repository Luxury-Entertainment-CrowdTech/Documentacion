# ALTERNATIVAS A SEAL DE MICROSOFT

## HElib (Homomorphic Encryption library)
Aunque originalmente enfocado en el cifrado parcialmente homomórfico, HElib ha evolucionado y ahora incluye soporte para ciertas formas de cifrado totalmente homomórfico. Es ampliamente utilizado en la investigación.

## TFHE (Fast Fully Homomorphic Encryption over the Torus)
Es una de las bibliotecas más conocidas específicamente diseñada para el cifrado totalmente homomórfico. TFHE se destaca por su enfoque en la eficiencia de las operaciones a nivel de bits lo que permite construir operaciones aritméticas y lógicas complejas a partir de operaciones más simples.

## FHEW (Fast Homomorphic Encryption over the Word)
Como una alternativa a TFHE, FHEW también ofrece cifrado totalmente homomórfico con un enfoque en la eficiencia pero con diferencias en la implementación que pueden hacerla más adecuada para ciertos casos de uso.

## SEAL (Simple Encrypted Arithmetic Library)
A pesar de ser desarrollado por Microsoft, es importante mencionarlo nuevamente ya que SEAL es muy versátil y soporta operaciones de cifrado totalmente homomórfico además de ser uno de los proyectos más activos y mantenidos en el ámbito de FHE.

## PALISADE
Esta biblioteca soporta una amplia variedad de esquemas de cifrado incluyendo el cifrado totalmente homomórfico. PALISADE es notable por su enfoque en la flexibilidad y en proporcionar un marco para la investigación y el desarrollo de aplicaciones que requieren FHE.

## Lattigo
Es otra biblioteca que ha añadido soporte para esquemas de cifrado totalmente homomórfico recientemente. Está escrita en Go y se centra en ofrecer una implementación eficiente de FHE.

Cada una de estas opciones tiene sus propias características y ventajas dependiendo de los requisitos específicos del proyecto. TFHE y FHEW se destacan por su eficiencia en operaciones a nivel de bits lo que las hace particularmente útiles para aplicaciones que requieren una gran cantidad de operaciones lógicas sobre datos cifrados. HElib, SEAL, PALISADE y Lattigo ofrecen una gama más amplia de funcionalidades y pueden ser más adecuados para aplicaciones que necesitan realizar operaciones aritméticas complejas sobre datos cifrados.

# ¿Como instalarlas?

## HElib
Requiere las siguientes dependencias para su instalación y configuración:
- m4 versión 1.4.16 o superior.
- patchelf versión 0.9 o superior (solo para Linux).

La instalación puede seguir dos enfoques: un build de paquete o un build de biblioteca. Para un build de paquete necesitarás ejecutar varios pasos en la terminal que incluyen la creación de un directorio de build, la configuración mediante cmake y finalmente la compilación y la instalación opcional de pruebas. Este enfoque empaqueta HElib y sus dependencias juntas, lo que permite una mayor portabilidad.

Para un build de biblioteca, que es un enfoque más avanzado, se construye HElib por sí mismo, enlazándolo contra las dependencias preexistentes en el sistema, específicamente GMP (versión 6.0.0 o superior) y NTL (versión 11.4.3 o superior). Este método requiere que instales GMP y NTL por tu cuenta, configurando variables de entorno para apuntar a sus directorios de instalación.

HElib fue desarrollado principalmente por Shai Halevi y Victor Shoup poco después de que Craig Gentry trabajara como investigador en IBM, con su primera versión lanzada el 5 de mayo de 2013. HElib está escrito en C++ y utiliza la biblioteca matemática NTL. Implementa el esquema de cifrado totalmente homomórfico de Brakerski-Gentry-Vaikuntanathan (BGV), así como optimizaciones como las técnicas de empaquetamiento de ciphertexts de Smart-Vercauteren.

HElib es una biblioteca para el lenguaje de programación C++. Existe un envoltorio de HElib para Python encontrado en GitHub bajo el nombre "HElib-python-wrapper", aunque parece ser un proyecto con limitada información y documentación disponible. [https://github.com/simenbakke/HElib-python-wrapper](https://github.com/simenbakke/HElib-python-wrapper)

## TFHE
Para instalar la biblioteca TFHE necesitarás cmake y un compilador C++ actualizado como g++ (versión 5.2 o superior) o clang (versión 3.8 o superior). En Debian/Ubuntu puedes instalar estas herramientas con `sudo apt-get install build-essential cmake cmake-curses-gui`. La configuración y construcción se realiza clonando el repositorio de TFHE, creando un directorio de construcción y luego usando ccmake para configurar las opciones de construcción antes de compilar e instalar la biblioteca.[https://tfhe.github.io/tfhe/installation.html](https://tfhe.github.io/tfhe/installation.html)

TFHE es una biblioteca para el lenguaje de programación C++. No se encontró wrappers para otros lenguajes.

## FHEW
Para instalar FHEW necesitas la biblioteca FFTW 3 y un compilador C++. El proceso de instalación es sencillo: ejecutas `make` para construir la biblioteca y los programas de prueba/ejemplo. Para instalar los archivos de cabecera y la biblioteca de FHEW, usas make install, que por defecto instala en los directorios $(HOME)/include y $(HOME)/lib, aunque puedes editar el Makefile según tus necesidades. [https://github.com/lducas/FHEW/tree/master](https://github.com/lducas/FHEW/tree/master)

FHEW es una biblioteca para el lenguaje de programación C++. No se encontró wrappers para otros lenguajes.

## PALISADE
Para instalar PALISADE, necesitas tener un compilador C++ con soporte para OMP, cmake, make y autoconf. El proceso de instalación implica clonar el repositorio de PALISADE, descargar submódulos git, crear un directorio de construcción, y luego usar CMake y make para construir la biblioteca. PALISADE soporta Linux, Windows y macOS, y está disponible bajo la licencia BSD de 2 cláusulas. [https://github.com/yamanalab/PALISADE](https://github.com/yamanalab/PALISADE)

PALISADE es una biblioteca para el lenguaje de programación C++. Existen wrappers de Python para PALISADE que permite utilizar algunas de sus funcionalidades desde Python. [https://github.com/Hoseung/palisade_python_test](https://github.com/Hoseung/palisade_python_test) y [https://gitlab.com/palisade/palisade-python-demo](https://gitlab.com/palisade/palisade-python-demo)

## Lattigo
Es una biblioteca Go que implementa criptografía homomórfica basada en el aprendizaje con errores en anillos. Está diseñada para ser una implementación pura de Go, lo que facilita la construcción en varias plataformas, incluida la compilación WASM para clientes de navegador. La versión específica mencionada es Lattigo v2.4.1 y está licenciada bajo Apache 2.0. No se detallan dependencias específicas fuera del ecosistema Go, lo que sugiere que las dependencias son manejadas a través del sistema de módulos de Go.

Para instalar Lattigo, debes tener instalado Go en tu sistema. Luego, puedes instalar Lattigo como un módulo de Go utilizando el comando go get seguido de la ruta del repositorio de Lattigo. Por ejemplo, para una versión específica, usarías algo como go get github.com/ldsec/lattigo/v2 para la versión 2.x.x de Lattigo. Este comando descarga e instala la biblioteca Lattigo y sus dependencias en tu entorno Go. [https://pkg.go.dev/github.com/ldsec/lattigo/v2](https://pkg.go.dev/github.com/ldsec/lattigo/v2)

Lattigo es una biblioteca para el lenguaje de programación Go. No se encontró wrappers para otros Python, solo para c++. [https://github.com/awslabs/aws-cppwrapper-lattigo](https://github.com/awslabs/aws-cppwrapper-lattigo)

## SEAL
Para instalar Microsoft SEAL, necesitas CMake y un compilador de C++ compatible. SEAL está diseñado para ser fácil de construir y usar en múltiples plataformas, incluyendo Windows, Linux y macOS. La documentación oficial de SEAL proporciona instrucciones detalladas de instalación para diferentes sistemas operativos. No se mencionan dependencias externas complejas, lo que facilita su integración en proyectos existentes. Para obtener instrucciones específicas y actualizadas, siempre es mejor consultar la documentación oficial de Microsoft SEAL en su repositorio de GitHub. [https://github.com/microsoft/SEAL](https://github.com/microsoft/SEAL)

Microsoft SEAL está desarrollado por Microsoft y está escrito en C++, pero está diseñado para ser accesible desde C# a través de .NET, ya que Microsoft proporciona soporte y documentación para su uso en aplicaciones .NET. Esto facilita su integración en proyectos basados en C#, permitiendo a los desarrolladores utilizar las capacidades de cifrado homomórfico directamente en sus aplicaciones C# sin necesidad de wrappers adicionales.

Microsoft SEAL tiene wrappers para Python. PySEAL es un ejemplo popular de un wrapper de Python para Microsoft SEAL, permitiendo a los usuarios acceder a las funcionalidades de cifrado homomórfico de SEAL desde Python. 

PySEAL y TenSEAL son ambos proyectos que ofrecen interfaces de Python para trabajar con cifrado homomórfico, específicamente con bibliotecas como Microsoft SEAL. La principal diferencia entre ambos radica en su enfoque y funcionalidades específicas. PySEAL es un wrapper directo de Python para Microsoft SEAL, ofreciendo una manera de utilizar las funcionalidades de SEAL en Python. TenSEAL, por otro lado, se centra en operaciones de cifrado homomórfico sobre tensores, optimizado para aplicaciones de aprendizaje automático, proporcionando una API de alto nivel para trabajar con datos cifrados en contextos de ML.
