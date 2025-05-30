# Reflection on Hello Minikube

## 1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
Jumlah log akan bertambah setiap kali aplikasi diakses melalui Service karena setiap permintaan menghasilkan entri log baru. Hal ini berarti service dan proxy berhasil meneruskan permintaan ke aplikasi dan aplikasi merespon sesuai permintaan tersebut.

## 2. Notice that there are two versions of kubectl get invocation during this tutorial section. The first does not have any option, while the latter has -n option with value set to kube-system. What is the purpose of the -n option and why did the output not list the pods/services that you explicitly created?
Perintah kubectl get tanpa menyertakan opsi -n hanya akan menampilkan resource yang berada di namespace default, yaitu namespace standar tempat Kubernetes menyimpan resource yang kita buat seperti Pod dan Service. Sedangkan perintah kubectl get -n kube-system digunakan untuk melihat resource yang berada di namespace kube-system yang dikhususkan untuk komponen internal Kubernetes. 

# Reflection on Rolling Update & Kubernetes Manifest File

## 1. What is the difference between Rolling Update and Recreate deployment strategy?
Perbedaan utama antara deployment Rolling Update dan Recreate terletak pada cara mereka mengganti versi aplikasi. Pada strategi Rolling Update, Pods lama akan digantikan secara bertahap dengan Pod baru, sehingga aplikasi tetap berjalan dan tidak mengalami downtime selama proses pembaruan. Sementara itu, strategi Recreate akan terlebih dahulu menghentikan semua Pod versi lama lalu menjalankan Pod versi baru, sheinggga menyebabkan downtime karena tidak ada Pod yang aktif selama proses transisi tersebut. 
## 2. Try deploying the Spring Petclinic REST using Recreate deployment strategy and document your attempt.
![image](https://github.com/user-attachments/assets/d075baa2-5c4a-4df8-a7e4-b984619c635d)


## 3. Prepare different manifest files for executing Recreate deployment strategy.
Saya menyiapkan deployment-recreate.yaml untuk konfigurasi deployment dengan strategi Recreate dan service-recreate.yaml untuk mengekspose aplikasi

## 4. What do you think are the benefits of using Kubernetes manifest files? Recall your experience in deploying the app manually and compare it to your experience when deploying the same app by applying the manifest files (i.e., invoking kubectl apply -f command) to the cluster.
Dengan menggunakan manifest files, saya dapat dengan mudah mempipeline perintahnya dibandingkan menulisnya satu persatu. Selain itu, file manifest juga dapat ditrack dengan version control sehingga dapat ditrack. Terakhir, saya dapat menjalankannya dengan cepat di environtment mana saja di luar komputer saya.
