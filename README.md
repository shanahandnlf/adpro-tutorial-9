Reflection
 1. What are the key differences between unary, server streaming, and bi-directional streaming 
 RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

Dalam Unary RPC adalah RPC paling sederhana, di mana klien mengirimkan permintaan ke server dan menerima respons tunggal. RPC ini cocok untuk kasus di mana klien hanya perlu mengirimkan permintaan sekali dan menerima respons tunggal dari server.

Server streaming RPC adalah RPC di mana klien mengirimkan permintaan ke server dan menerima respons yang berkelanjutan dalam bentuk "stream of data". RPC ini cocok untuk kasus di mana klien perlu menerima data yang berkelanjutan dari server, seperti mengunduh file atau streaming video.

Bidirectional streaming RPC adalah RPC di mana klien dan server saling berinteraksi dengan mengirimkan dan menerima data dalam bentuk aliran data. RPC ini cocok untuk kasus di mana klien dan server perlu berkomunikasi secara real-time dan saling bertukar data dalam bentuk aliran, seperti aplikasi obrolan atau permainan real-time.

 2. What are the potential security considerations involved in implementing a gRPC service in
 Rust, particularly regarding authentication, authorization, and data encryption?

Dalam mengimplementasikan layanan gRPC di Rust, beberapa pertimbangan keamanan yang perlu antara lain seperti autentikasi, autorisasi. Autentikasi digunakan untuk memverifikasi identitas klien dan server, memastikan bahwa klien dan server yang berkomunikasi adalah yang seharusnya. Autorisasi digunakan untuk mengontrol akses klien ke sumber daya atau layanan tertentu berdasarkan hak akses yang dimiliki.


 3. What are the potential challenges or issues that may arise when handling bidirectional
 streaming in Rust gRPC, especially in scenarios like chat applications?

Dalam streaming bidirectional dalam rust, tantangan yang mungkin muncul dapat berupa sinkronisasi antara klien dan server dan error handling. Sinkronisasi antara klien dan server penting untuk memastikan bahwa data yang dikirim dan diterima oleh klien dan server sesuai dengan urutan yang benar. Error handling juga penting untuk menangani situasi di mana terjadi kesalahan dalam komunikasi atau pemrosesan data.


 4. What are the advantages and disadvantages of using the
 tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?

 Keuntungan: ReceiverStream compatible dengan tokio, sehingga memungkinkan untuk mengintegrasikan dengan baik dengan kode tokio lainnya. ReceiverStream juga menyediakan berbagai metode dan fungsi yang berguna untuk memanipulasi aliran data, seperti map, filter, dan fold. Operasi asynchronous yang mudah digunakan dan dapat diintegrasikan dengan baik dengan kode Rust gRPC lainnya.

Kekurangan: ReceiverStream lebih kompleks dan memerlukan pemahaman yang lebih dalam tentang konsep-konsep asynchronous programming di Rust. ReceiverStream juga memerlukan penanganan error yang lebih cermat dan kompleks, karena operasi asynchronous dapat menghasilkan error yang sulit untuk diidentifikasi dan ditangani.

 5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity,
 promoting maintainability and extensibility over time?

 Pemisahan modul seperti layanan grpc services.proto dan implementasi grpc bagian klient dan server. Dengan memisahkan modul, kode dapat diorganisir dengan lebih baik dan memungkinkan untuk mengelola dependensi antara berbagai bagian kode dengan lebih efisien. Selain itu, menggunakan trait dan struct untuk mengabstraksi fungsionalitas umum dan mempromosikan reusabilitas kode. 


 6. In the MyPaymentService implementation, what additional steps might be necessary to
 handle more complex payment processing logic?

Validasi data yang lebih ketat, seperti memeriksa apakah data pembayaran valid dan lengkap sebelum memproses pembayaran dan menangani kasus-kasus error yang lebih kompleks, seperti pembayaran yang gagal atau transaksi yang tidak lengkap. Selain itu, menambahkan logging dan monitoring untuk melacak dan menganalisis kinerja sistem dan menangani kasus error yang tidak terduga.

 7. What impact does the adoption of gRPC as a communication protocol have on the overall
 architecture and design of distributed systems, particularly in terms of interoperability with
 other technologies and platforms?

 Penggunaan grpc memudahkan interaksi antara berbagai layanan dan platform, karena grpc menggunakan protokol HTTP/2 yang mendukung komunikasi yang efisien dan cepat. Dengan menggunakan grpc, sistem terdistribusi dapat berkomunikasi dengan lebih efisien dan dapat diintegrasikan dengan teknologi dan platform lainnya yang mendukung protokol HTTP/2. 


 8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for
 gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

Keuntungan HTTP/2: Kemampuan mengelola multiple requests dan responses secara paralel, kompresi header, dan server push. HTTP/2 juga mendukung streaming data, yang memungkinkan untuk mengirim dan menerima data secara real-time. Kecepatan dan efisiensi komunikasi yang lebih baik, terutama untuk aplikasi yang memerlukan komunikasi yang cepat dan efisien.

Kekurangan HTTP/2: Kompleksitas implementasi yang lebih tinggi, karena HTTP/2 memiliki fitur-fitur yang lebih kompleks dan memerlukan pemahaman yang lebih dalam tentang protokol tersebut. Dibandingkan dengan HTTP/1.1 atau HTTP/1.1 dengan WebSocket, HTTP/2 juga memerlukan dukungan server dan klien yang lebih canggih untuk mengimplementasikan fitur-fitur seperti server push dan streaming data.


 9. How does the request-response model of REST APIs contrast with the bidirectional streaming
 capabilities of gRPC in terms of real-time communication and responsiveness?

Model request-response pada REST API adalah model sederhana di mana klien mengirim request ke server dan menerima response dari server. Model ini cocok untuk kasus di mana klien hanya perlu mengirim request sekali dan menerima response tunggal dari server. Dalam model ini, komunikasi real-time dan responsif terbatas oleh klien yang harus mengirim request untuk menerima response dari server. Sedangkan, gRPC dengan streaming bidirectional memungkinkan klien dan server untuk saling berinteraksi secara real-time dan bertukar data dalam bentuk stream. Model ini lebih responsif dan memungkinkan komunikasi real-time yang lebih baik antara klien dan server.


 10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers,
 compared to the more flexible, schema-less nature of JSON in REST API payloads?

Pendekatan berbasis skema gRPC menggunakan Protocol Buffers memungkinkan untuk mendefinisikan skema data yang ketat dan jelas, serta memungkinkan untuk validasi data yang dilakukan secara otomatis. Dengan menggunakan skema data yang ketat, gRPC dapat memastikan bahwa data yang dikirim dan diterima oleh klien dan server sesuai dengan format yang diharapkan. Di sisi lain, pendekatan JSON dalam REST API memungkinkan untuk fleksibilitas yang lebih besar dalam format data, karena JSON adalah format data yang lebih umum dan mudah dibaca oleh manusia. Namun, JSON tidak memiliki skema data yang ketat, sehingga memerlukan validasi data yang lebih cermat dan kompleks.

