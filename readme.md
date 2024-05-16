## Refleksi Deployment Kubectl (Tutorial 11)
### Refleksi Pertama

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?

![](docs/service-application-log.png)
Sebelum diexposed sebagai service, tentu saja kita tidak dapat mengakses pod tersebut dari luar cluster. Sementara itu, setelah diexposed sebagai service, kita dapat mengakses pod tersebut dari luar cluster melalui external ip yang kita tempelkan pada service tersebut. Dengan mengakses external ip tersebut maka log aplikasi akan bertambah untuk menghandle koneksi yang masuk ke external ip tersebut.

2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. he first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that youexplicitly created? > Hint: Do some reading about [Namespace in Kubernetes document].

Opsi `-n` pada perintah `kubectl get` digunakan untuk menentukan namespace di mana Anda ingin melihat sumber daya. Dalam Kubernetes, namespace adalah cara untuk membagi sumber daya dalam sebuah kluster antara beberapa pengguna. Ketika Anda menjalankan `kubectl get` tanpa opsi apapun, perintah ini secara default akan menampilkan sumber daya di namespace `default`.