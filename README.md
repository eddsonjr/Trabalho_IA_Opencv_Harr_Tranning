      Criado por: Edson Jr                 
      Novembro de 2016                     
      

        


# Trabalho_IA_Opencv_Haar_Cascade_Tranning

Encontra - se neste repositório um conjunto de algoritmos destinados a tratar imagens para posteriormente serem treinadas utilizando o algoritmo de Haar Cascade. Para tanto foi utilizado o Opencv na sua versão 2.4.9. Para maiores informações, leia o 'Read-me' posto neste repositório. O repositório também conta com arquivos de cascade já treinados, com imagens positivas, negativas e de testes. 


#Introdução
Neste repositório encontram - se os arquivos utilizados em um trabalho de Inteligência Artificial, cujo objetivo era criar e 
descrever o reconhecimento de padrões, com foco especial no reconhecimento facial. Para tanto, foi - se utilizado o Opencv (versão 2.4.9) e o algoritmo de Haar Cascade para treinar um padrão de rosto a ser reconhecido. Todos os algortimos foram escritos usando a IDE Xcode 8.0, cuja configuração com o Opencv será abordada mais adiante.

#Conteúdo

Dentro deste repositório você encontrará três projetos do Xcode, cada um com uma finalidade específica no que diz respeito ao 
preparo das imagens e ao reconhecimento do padrão treinado; imagens positivas, negativas e de testes; arquivos de cascade.xml e arquivos de suporte ao treinamento. Também encontrará um pequeno relatório descrevendo o experimento realizado. 

Conteúdo descrito:

- Imagens/negativas -> Imagens negativas usadas no treinamento.
- Imagens/positivas -> Imagens positivas usadas no treinamento.
- Imagens/teste -> Imagens de testes
- Classificadores/  -> contem várias pastas, cada qual com um classificador treinado com quantidade de estágios diferentes
- C_G_Images/ -> contem arquivos do projeto do Xcode, cujo algortimo é responsável por detectar uma face, recotar tal face e também deixá - la em escala de cinza. A imagem tratada é salva no disco. (IMPORTANTE: tal algoritmo utiliza Opencv)
- D_N_Images/ -> contem arquivos do projeto do Xcode, cujo algortimo é responsável por duplicar imagens e, caso queira, aplicar alguns filtros básicos, como blur e bilateral. O conteúdo da imagem tratada é salvo em disco. (IMPORTANTE: tal algoritmo utiliza Opencv).
- TestCustonHaar/ -> contem arquivos do projeto do Xcode, cujo algoritmo solicita um arquivo cascade.xml e uma imagem de entrada, verificando se o padrão do arquivo cascade.xml foi ou não encontrado na imagem. (IMPORTANTE: tal algoritmo utiliza Opencv)

- bg.txt -> arquivo contendo paths das imagens negativas (com base nas imagens desse repositório).
- positivasDAT.txt -> arquivo contendo paths e regiões das imagens positivas a serem treinadas (com base nas imagens desse repositório).

- Samples.vec -> arquivo vec (binário das imagens positivas) criados pelo opencv_createsamples.



#Comandos do Opencv
Abaixo estão listados os comandos básicos utilizados pelo Opencv para o treinamento (com base no conteúdo deste repositório).

*opencv_createsamples:* 

opencv_traincascade -info positivasDAT.txt -bg bg.txt -num 1010 -vec Samples.vec  -num 1010 -h 32 -w 32


*opencv_traincascade:*

opencv_traincascade -data classifier -vec Samples.vec -bg bg.txt -numPos 1010 -numNeg 2990  -numStages 16 -precalcValBufSize 2048 -precalcIdxBufSize 2048 -w 32 -h 32 -minHitRate 0.9 -minHitRate  0.47 -mode ALL 

Importante: O processo de treinamento poderá demorar várias horas ou até dias dependendo da quantidade de imagens a serem treinadas, quantidade de estágios e a dimensão das imagens, além claro do hardware utilizado.



#Configurando o Xcode 
As informações desta seção foram retiradas do site: (http://blogs.wcode.org/2014/11/howto-setup-xcode-6-1-to-work-with-opencv-libraries/)

De forma resumida: 
Procure por **Header Search Paths** e adicione a seguinte linha: /usr/local/include

Procure por **Library Search Paths** e adicione a seguinte linha:  /usr/local/lib

Procure por **Other Linker Flags** e adicione as seguintes opeções: -lopencv_calib3d -lopencv_core -lopencv_features2d -lopencv_flann -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_shape -lopencv_stitching -lopencv_superres -lopencv_ts -lopencv_video -lopencv_videoio -lopencv_videostab

Importante: caso o Xcode não encontre alguma das opções acima, basta removê-la da configuração.



