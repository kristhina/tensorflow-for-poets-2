# How To Use It

1. Download the repo from GitHub
```
git clone https://github.com/kristhina/tensorflow-for-poets-2.git
```
2. Change directory to "tensorflow-for-poets-2"
```
cd tensorflow-for-poets-2
```
3. Install Python packages from the requirements.txt
```
pip install -r requirements.txt
```
4. To classify an image `to_check/04_06_2_004.jpg` run the following command:
```
python -m scripts.label_image \
--graph=tf_files/retrained_graph.pb \
--image=tf_files/to_check/04_06_2_004.jpg
```
This is the example of Neglyubka picture.
You can change the name of file to test other patterns:
* `01_01_2_036.jpg` (Gzhel)
* `01_02_2_039.jpg` (Khlokhloma)
* `02_04_2_022.jpg` (Wycinanki Łowickie)
* `01_03_2_053.jpg` (Gorodets)
* `02_07_2_012.jpg` (Wzory Kaszubskie)
* `03_05_2_020.jpg` (Iznik)

I also prepared some more pictures from Internet (you can find them in the folder "to_check")

# My Workflow

1. Forked and Cloned the repo TensorFlow For Poets from GitHub
2. Created new VirtualEnv and installed Tensorflow
3. Set environment variables:
  ``` 
  export IMAGE_SIZE=224
  export ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"
  ```
4. Downloaded the pictures from kaggle.com
5. Unpacked the pictures
6. Changed the format from png to jpg:  `mogrify -format jpg *.png`
7. Prepared folders for each type of pictures (Gzhel, Khokhloma, Gorodets, Wycinanki_lowickie, Wzory_kaszubskie, Iznik, Neglyubka)
8. From each file I chose one picture to test the model (folder "to_check") - I decided to choose only one picture from each folder because there are not many of them to teach the network. When I wanted to check another picture - I could download it from the Internet
9. Prepared three different models to teach the network:
  * "pattern + product" (I used both pattern and product pictures to teach the network and checked if it could recognize correctly the product pictures)
  * "pattern" (I used only pattern pictures to teach the network and checked if it could find patterns on the product pictures)
  * "product" (I used only product pictures to teach the network)
10. Trained the network (with 500 training steps) and achieved the following results:
  * pattern + product 79,5% final test accuracy
  * pattern 90% final test accuracy
  * product 72,2% final test accuracy
11. Checked the pictures in my folder "to_check" - results for "pattern" model were the worstgit status. There were not great differences between "pattern+product" and "product" results. The product results were slightly better, but I had only one picture from each decor to check
12. Downloaded some picture from the Internet to check my network
13. Decided to choose the model with "pattern+product":
  * there are more pictures to train the network
  * there were no great differences between the models when I was checking the resulst on my selected pictures
  * final test accuracy was better
14. Retrained the network without the step limit (default 4000 iterations) - final test accuracy was also 79,5%. 
15. Checked the charts from TensorBoard









