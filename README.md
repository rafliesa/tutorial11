# Reflection on Hello Minikube

## 1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
Jumlah log akan bertambah setiap kali aplikasi diakses melalui Service karena setiap permintaan menghasilkan entri log baru. Hal ini berarti service dan proxy berhasil meneruskan permintaan ke aplikasi dan aplikasi merespon sesuai permintaan tersebut.

## 2. Notice that there are two versions of kubectl get invocation during this tutorial section. The first does not have any option, while the latter has -n option with value set to kube-system. What is the purpose of the -n option and why did the output not list the pods/services that you explicitly created?
Perintah kubectl get tanpa menyertakan opsi -n hanya akan menampilkan resource yang berada di namespace default, yaitu namespace standar tempat Kubernetes menyimpan resource yang kita buat seperti Pod dan Service. Sedangkan perintah kubectl get -n kube-system digunakan untuk melihat resource yang berada di namespace kube-system yang dikhususkan untuk komponen internal Kubernetes. 
