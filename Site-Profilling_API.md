# API Site Profilling

#### Postman
<a href="site-profilling.postman_collection.json" download>Download Postman Collection</a>

## HTTP Request Login
```URL
POST http://52.221.228.196:3030/users/login
```


#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| username   | required	  	| `username` dari aplikasi	   |
| password   | required	  	| `password` dari aplikasi 	   |


#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|message|menandakan login berhasil atau tidak|
|token|token yang digenerate|
|email_username|email atau username yang digunakan untuk login|
|refreshToken|token yang digenerate|
|request|informasi jenis request|



#### Request
```json
curl --location --request POST 'http://52.221.228.196:3030/users/login' \
--header 'Content-Type: application/json' \
--data-raw '{
	"email_username" : $USERNAME,
	"password" : $PASSWORD
}'
```

#### Respon
```json
{
    "message": "Auth successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ODcsImVtYWlsIjoiYWRtaW5AZ21haWwuY29tIiwiZmlyc3RuYW1lIjoiU3VwZXIiLCJsYXN0bmFt",
    "email_username": "123",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ODcsImVtYWlsIjoiYWRtaW5AZ21haWwuY29tIiwiZmlyc3RuYW1lIjoiU3VwZXIiLCJsYXN0bmFt",
    "testCICD": "oke",
    "request": {
        "type": "POST",
        "url": "/users"
    }
}
```


## HTTP Request Site Profilling
```URL
POST http://52.221.228.196:5030/api/v1.0/drivetime
```

#### Header

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| client_id   | required	  	|  `431322697`	   |
| client_secret  | required	  	|  `U2FsdGVkX19cQ7QtXcaKmNAUxPltu1ct/e2li65h64aNEfPCXsIwJo+Tg48NNAIh2LF+binkHw9HHsjTntgoYvlPzSlOthlUKawuX6xYWM9ptUKeL0xmR3kwtUDvjSSN`  	   |
| Authorization   | required	  	|  `Authorization` didapatkan dengan cara login  	   |


#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| coordinate   | required	  	| `name` nama dari titik koordinat 	   |
|                 | required	  	| `coordinate` koordinate yang berupa longitude, latitude	   |

#### Result

| Parameters  |  |  Description  |
| -------------|--- |--------------|
|nama titik| |`"Site 1":` nama titik yang diinpun dari request|
|area/point|area |isochrones dan informasi areanya|
||point|berisi POI|
|jarak ishochrones/ buffer| |jarak dari setiap isochrones atau buffer|
|feature| |geojson yang berisi geometry dan properties|

`
`

| tipe | feature properties |  Description  |
| -------------|--- |--------------|
|area| Household| jumlah KK|
||age |jumlah orang setiap golongan umur |
||demography | jumlah orang berdasarkan jenis kelamin|
|| driving_unit|satuan jarah isochrones |
||durasi_distance | waktu tempuh jarak isochrones |
||kabupaten |nama kabupaten|
||kecamatan | nama kecamatan|
||nama_desa | namadesa|
||kodepodes | kode podes|
||latitude | latitude titik tengah|
||longitude | longitude titik tengah|
||luas_m | luas isochrones|
||poi | statistik POI di dalan ishochrones|
||provinsi | nama provinsi|
||ses | statistik SES|
||tipe_driving | jenis isochrones|
||zone | peraturan zonasi di dalan izochrones|
|point|alamat_merchant|alamat dari POI|
|| developer_name| nama developer dari POI, `null` apabila tidak ada informasi|
|| dist| jarak POI dari titik tengah|
|| id_brand| id brad dari POI|
||id_merchant |id dari POI |
||kode_brand|kode brand POI |
||kode_kategori |kode kategori POI |
||kode_sub_kategori |kode sub kategori POI |
||latitude | latitude dari POI|
||longitude |longitude dari POI |
||nama_brand | nama brand POI|
|| nama_merchant| nama POI|
||number_of_parking | jumlah tempat parkir di POI,  `null` apabila tidak ada informasi |
|| parking_fees|harga parkir di POI,  `null` apabila tidak ada|
||phone_merchant | nomor telepon POI,  `null` apabila tidak ada|
||subclass | nama sub kelas dari POI |


### Example

#### Request
```json
curl --location --request POST 'http://52.221.228.196:5030/api/v1.0/drivetime' \
--header 'client_id: 431322697' \
--header 'client_secret: U2FsdGVkX19cQ7QtXcaKmNAUxPltu1ct/e2li65h64aNEfPCXsIwJo+Tg48NNAIh2LF+binkHw9HHsjTntgoYvlPzSlOthlUKawuX6xYWM9ptUKeL0xmR3kwtUDvjSSN' \
--header 'Authorization: $AUTHORIZATION' \
--header 'Content-Type: application/json' \
--data-raw '{
    "coordinate": [
        {
            "name": "Gading Serpong",
            "coordinate": [
               106.628007,-6.246553 //gading serpong
            ]
        }
    ]
}'
```
#### Response
<details>
<summary>

```json
{
    "Site 1": {
        "area": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.862566,
                                        -6.172418
                                    ],
                                    [
                                        106.863222,
                                        -6.170092
```

</summary>

```json


{
    "Site 1": {
        "area": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.862566,
                                        -6.172418
                                    ],
                                    [
                                        106.863222,
                                        -6.170092
                                    ],
                                    [
                                        106.86623,
                                        -6.159311
                                    ],
                                    [
                                        106.865938,
                                        -6.157834
                                    ],
                                    [
                                        106.866313,
                                        -6.156831
                                    ],
                                    [
                                        106.867021,
                                        -6.145456
                                    ],
                                    [
                                        106.870632,
                                        -6.135933
                                    ],
                                    [
                                        106.871103,
                                        -6.135847
                                    ],
                                    [
                                        106.876987,
                                        -6.13568
                                    ],
                                    [
                                        106.881782,
                                        -6.128109
                                    ],
                                    [
                                        106.882511,
                                        -6.124583
                                    ],
                                    [
                                        106.891335,
                                        -6.119181
                                    ],
                                    [
                                        106.893029,
                                        -6.117613
                                    ],
                                    [
                                        106.893077,
                                        -6.117611
                                    ],
                                    [
                                        106.894934,
                                        -6.119233
                                    ],
                                    [
                                        106.894931,
                                        -6.119437
                                    ],
                                    [
                                        106.894664,
                                        -6.121313
                                    ],
                                    [
                                        106.894237,
                                        -6.123689
                                    ],
                                    [
                                        106.893915,
                                        -6.125807
                                    ],
                                    [
                                        106.895434,
                                        -6.134217
                                    ],
                                    [
                                        106.90135,
                                        -6.141305
                                    ],
                                    [
                                        106.906793,
                                        -6.142223
                                    ],
                                    [
                                        106.914582,
                                        -6.135945
                                    ],
                                    [
                                        106.916357,
                                        -6.131028
                                    ],
                                    [
                                        106.916479,
                                        -6.130804
                                    ],
                                    [
                                        106.917583,
                                        -6.130759
                                    ],
                                    [
                                        106.917974,
                                        -6.130894
                                    ],
                                    [
                                        106.919639,
                                        -6.132529
                                    ],
                                    [
                                        106.923748,
                                        -6.141526
                                    ],
                                    [
                                        106.926174,
                                        -6.145146
                                    ],
                                    [
                                        106.931347,
                                        -6.155805
                                    ],
                                    [
                                        106.926684,
                                        -6.165554
                                    ],
                                    [
                                        106.92649,
                                        -6.1659
                                    ],
                                    [
                                        106.924562,
                                        -6.170567
                                    ],
                                    [
                                        106.926595,
                                        -6.181734
                                    ],
                                    [
                                        106.927828,
                                        -6.183482
                                    ],
                                    [
                                        106.927839,
                                        -6.183566
                                    ],
                                    [
                                        106.927675,
                                        -6.184062
                                    ],
                                    [
                                        106.927146,
                                        -6.185292
                                    ],
                                    [
                                        106.925261,
                                        -6.18605
                                    ],
                                    [
                                        106.921016,
                                        -6.185404
                                    ],
                                    [
                                        106.913912,
                                        -6.184315
                                    ],
                                    [
                                        106.913598,
                                        -6.184306
                                    ],
                                    [
                                        106.911883,
                                        -6.183995
                                    ],
                                    [
                                        106.911784,
                                        -6.183972
                                    ],
                                    [
                                        106.910295,
                                        -6.183514
                                    ],
                                    [
                                        106.899433,
                                        -6.187094
                                    ],
                                    [
                                        106.893065,
                                        -6.192155
                                    ],
                                    [
                                        106.891628,
                                        -6.192909
                                    ],
                                    [
                                        106.891382,
                                        -6.192926
                                    ],
                                    [
                                        106.889465,
                                        -6.192156
                                    ],
                                    [
                                        106.887565,
                                        -6.189408
                                    ],
                                    [
                                        106.876486,
                                        -6.189396
                                    ],
                                    [
                                        106.876386,
                                        -6.18947
                                    ],
                                    [
                                        106.875503,
                                        -6.189624
                                    ],
                                    [
                                        106.875233,
                                        -6.189616
                                    ],
                                    [
                                        106.873742,
                                        -6.188108
                                    ],
                                    [
                                        106.86986,
                                        -6.178026
                                    ],
                                    [
                                        106.864274,
                                        -6.173321
                                    ],
                                    [
                                        106.862595,
                                        -6.172484
                                    ],
                                    [
                                        106.862566,
                                        -6.172418
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "167,472",
                            "age": {
                                "0": {
                                    "persen": 16.03359468984344,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 80509.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 15.6721323146796,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 78694.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 14.834893843501199,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 74490.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 14.809003976409574,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 74360.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 16.36717566967784,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 82184.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 18.762784986948294,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 94213.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 18.721361199601695,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 94005.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 16.181366085089486,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 81251.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 13.388646037198262,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 67228.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 16.444646118128937,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 82573.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 10.395777401406397,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 52200.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 7.794244064345636,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 39137.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 6.7954926530802515,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 34122.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 3.4859710274754327,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 17504.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 502127,
                                    "persen": 49.81667984394386,
                                    "total": 250143
                                },
                                "male": {
                                    "from": 502127,
                                    "persen": 50.18332015605613,
                                    "total": 251984
                                },
                                "total": {
                                    "from": 3294701,
                                    "persen": 15.24044215241383,
                                    "total": 502127
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 10.0,
                            "high": 0,
                            "kabupaten": "JAKARTA UTARA",
                            "kecamatan": "KELAPA GADING",
                            "ket": "Site 1",
                            "kodepodes": "3175050001",
                            "latitude": -682458.196,
                            "longitude": 11899593.496,
                            "low": 0,
                            "luas_m": 39700791590.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "KELAPA GADING BARAT",
                            "poi": {
                                "Apartment": {
                                    "kode_sub_kategori": "2601",
                                    "min_dist": 92.45990576,
                                    "tot": 30
                                },
                                "Bus Stop": {
                                    "kode_sub_kategori": "1110",
                                    "min_dist": 92.45990576,
                                    "tot": 54
                                },
                                "Office Building": {
                                    "kode_sub_kategori": "2603",
                                    "min_dist": 92.45990576,
                                    "tot": 14
                                },
                                "Senior High School": {
                                    "kode_sub_kategori": "1404",
                                    "min_dist": 92.45990576,
                                    "tot": 21
                                },
                                "Store": {
                                    "kode_sub_kategori": "1610",
                                    "min_dist": 92.45990576,
                                    "tot": 11
                                }
                            },
                            "provinsi": "DKI JAKARTA",
                            "ses": {
                                "high": 38.157000000000004,
                                "low": 25.971000000000004,
                                "medium_high": 28.954,
                                "medium_low": 6.9190000000000005
                            },
                            "tipe_driving": "driving-car",
                            "zone": [
                                "CAMPURAN",
                                "INDUSTRI DAN PERDAGANGAN/JASA",
                                "KAWASAN LINDUNG",
                                "PARIWISATA",
                                "PELAYANAN UMUM",
                                "PEMERINTAHAN",
                                "PERMUKIMAN",
                                "RUANG TERBUKA"
                            ]
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            },
            "15": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.809105,
                                        -6.128829
                                    ],
                                    [
                                        106.809475,
                                        -6.128731
                                    ],
                                    [
                                        106.813477,
                                        -6.127799
                                    ],
                                    [
                                        106.81703,
                                        -6.128598
                                    ],
                                    [
                                        106.82752,
                                        -6.123694
                                    ],
                                    [
                                        106.827572,
                                        -6.123672
                                    ],
                                    [
                                        106.829702,
                                        -6.123724
                                    ],
                                    [
                                        106.840547,
                                        -6.122249
                                    ],
                                    [
                                        106.845349,
                                        -6.120514
                                    ],
                                    [
                                        106.845797,
                                        -6.120417
                                    ],
                                    [
                                        106.851641,
                                        -6.119313
                                    ],
                                    [
                                        106.857897,
                                        -6.115515
                                    ],
                                    [
                                        106.858027,
                                        -6.115435
                                    ],
                                    [
                                        106.860821,
                                        -6.115798
                                    ],
                                    [
                                        106.8694,
                                        -6.110868
                                    ],
                                    [
                                        106.874257,
                                        -6.108972
                                    ],
                                    [
                                        106.878677,
                                        -6.100728
                                    ],
                                    [
                                        106.882223,
                                        -6.094064
                                    ],
                                    [
                                        106.885776,
                                        -6.094646
                                    ],
                                    [
                                        106.893281,
                                        -6.096096
                                    ],
                                    [
                                        106.902503,
                                        -6.098225
                                    ],
                                    [
                                        106.906926,
                                        -6.099102
                                    ],
                                    [
                                        106.914951,
                                        -6.100224
                                    ],
                                    [
                                        106.916374,
                                        -6.100719
                                    ],
                                    [
                                        106.926952,
                                        -6.099418
                                    ],
                                    [
                                        106.92728,
                                        -6.099414
                                    ],
                                    [
                                        106.936543,
                                        -6.100485
                                    ],
                                    [
                                        106.938357,
                                        -6.101588
                                    ],
                                    [
                                        106.941653,
                                        -6.104028
                                    ],
                                    [
                                        106.951257,
                                        -6.108311
                                    ],
                                    [
                                        106.951969,
                                        -6.110023
                                    ],
                                    [
                                        106.951968,
                                        -6.110129
                                    ],
                                    [
                                        106.951274,
                                        -6.111911
                                    ],
                                    [
                                        106.948389,
                                        -6.113337
                                    ],
                                    [
                                        106.948109,
                                        -6.113452
                                    ],
                                    [
                                        106.947922,
                                        -6.113455
                                    ],
                                    [
                                        106.937007,
                                        -6.115183
                                    ],
                                    [
                                        106.933885,
                                        -6.124925
                                    ],
                                    [
                                        106.935959,
                                        -6.130056
                                    ],
                                    [
                                        106.938643,
                                        -6.133033
                                    ],
                                    [
                                        106.941693,
                                        -6.138323
                                    ],
                                    [
                                        106.941777,
                                        -6.13855
                                    ],
                                    [
                                        106.942364,
                                        -6.144036
                                    ],
                                    [
                                        106.942369,
                                        -6.146223
                                    ],
                                    [
                                        106.949884,
                                        -6.155342
                                    ],
                                    [
                                        106.950631,
                                        -6.155606
                                    ],
                                    [
                                        106.953078,
                                        -6.156694
                                    ],
                                    [
                                        106.954175,
                                        -6.157325
                                    ],
                                    [
                                        106.954259,
                                        -6.157664
                                    ],
                                    [
                                        106.957021,
                                        -6.168716
                                    ],
                                    [
                                        106.963186,
                                        -6.170018
                                    ],
                                    [
                                        106.963279,
                                        -6.17002
                                    ],
                                    [
                                        106.964466,
                                        -6.170788
                                    ],
                                    [
                                        106.964532,
                                        -6.170923
                                    ],
                                    [
                                        106.970179,
                                        -6.178353
                                    ],
                                    [
                                        106.973766,
                                        -6.178657
                                    ],
                                    [
                                        106.974446,
                                        -6.179409
                                    ],
                                    [
                                        106.9787,
                                        -6.186587
                                    ],
                                    [
                                        106.979405,
                                        -6.196611
                                    ],
                                    [
                                        106.979395,
                                        -6.196672
                                    ],
                                    [
                                        106.976424,
                                        -6.202254
                                    ],
                                    [
                                        106.976406,
                                        -6.20226
                                    ],
                                    [
                                        106.975984,
                                        -6.202347
                                    ],
                                    [
                                        106.975965,
                                        -6.202348
                                    ],
                                    [
                                        106.968786,
                                        -6.200058
                                    ],
                                    [
                                        106.958749,
                                        -6.203021
                                    ],
                                    [
                                        106.957503,
                                        -6.207974
                                    ],
                                    [
                                        106.957463,
                                        -6.208112
                                    ],
                                    [
                                        106.952512,
                                        -6.215536
                                    ],
                                    [
                                        106.954813,
                                        -6.219982
                                    ],
                                    [
                                        106.95502,
                                        -6.226772
                                    ],
                                    [
                                        106.953421,
                                        -6.230924
                                    ],
                                    [
                                        106.949901,
                                        -6.230171
                                    ],
                                    [
                                        106.950468,
                                        -6.227514
                                    ],
                                    [
                                        106.951145,
                                        -6.224915
                                    ],
                                    [
                                        106.951213,
                                        -6.219982
                                    ],
                                    [
                                        106.94237,
                                        -6.212254
                                    ],
                                    [
                                        106.933983,
                                        -6.218858
                                    ],
                                    [
                                        106.930841,
                                        -6.227577
                                    ],
                                    [
                                        106.930848,
                                        -6.227639
                                    ],
                                    [
                                        106.929904,
                                        -6.229596
                                    ],
                                    [
                                        106.924704,
                                        -6.233523
                                    ],
                                    [
                                        106.923003,
                                        -6.2348
                                    ],
                                    [
                                        106.922806,
                                        -6.234801
                                    ],
                                    [
                                        106.921115,
                                        -6.233801
                                    ],
                                    [
                                        106.917438,
                                        -6.230132
                                    ],
                                    [
                                        106.913356,
                                        -6.223785
                                    ],
                                    [
                                        106.913295,
                                        -6.223734
                                    ],
                                    [
                                        106.904954,
                                        -6.220672
                                    ],
                                    [
                                        106.900898,
                                        -6.224566
                                    ],
                                    [
                                        106.899757,
                                        -6.225544
                                    ],
                                    [
                                        106.894024,
                                        -6.231318
                                    ],
                                    [
                                        106.887328,
                                        -6.241162
                                    ],
                                    [
                                        106.887246,
                                        -6.241221
                                    ],
                                    [
                                        106.885578,
                                        -6.241325
                                    ],
                                    [
                                        106.881793,
                                        -6.242546
                                    ],
                                    [
                                        106.876836,
                                        -6.250396
                                    ],
                                    [
                                        106.875433,
                                        -6.250961
                                    ],
                                    [
                                        106.872176,
                                        -6.249429
                                    ],
                                    [
                                        106.871653,
                                        -6.247979
                                    ],
                                    [
                                        106.872422,
                                        -6.240896
                                    ],
                                    [
                                        106.872411,
                                        -6.24072
                                    ],
                                    [
                                        106.872365,
                                        -6.240176
                                    ],
                                    [
                                        106.872362,
                                        -6.239939
                                    ],
                                    [
                                        106.86912,
                                        -6.229682
                                    ],
                                    [
                                        106.86552,
                                        -6.229733
                                    ],
                                    [
                                        106.865126,
                                        -6.226695
                                    ],
                                    [
                                        106.864573,
                                        -6.223138
                                    ],
                                    [
                                        106.85502,
                                        -6.216238
                                    ],
                                    [
                                        106.849511,
                                        -6.217296
                                    ],
                                    [
                                        106.844617,
                                        -6.21828
                                    ],
                                    [
                                        106.843161,
                                        -6.218472
                                    ],
                                    [
                                        106.843008,
                                        -6.218197
                                    ],
                                    [
                                        106.837839,
                                        -6.207946
                                    ],
                                    [
                                        106.836816,
                                        -6.205941
                                    ],
                                    [
                                        106.836879,
                                        -6.205746
                                    ],
                                    [
                                        106.837895,
                                        -6.202823
                                    ],
                                    [
                                        106.836946,
                                        -6.19271
                                    ],
                                    [
                                        106.836651,
                                        -6.191917
                                    ],
                                    [
                                        106.835325,
                                        -6.188794
                                    ],
                                    [
                                        106.831175,
                                        -6.183125
                                    ],
                                    [
                                        106.831106,
                                        -6.182985
                                    ],
                                    [
                                        106.829943,
                                        -6.180652
                                    ],
                                    [
                                        106.827321,
                                        -6.172987
                                    ],
                                    [
                                        106.827316,
                                        -6.172912
                                    ],
                                    [
                                        106.828753,
                                        -6.168095
                                    ],
                                    [
                                        106.832174,
                                        -6.15941
                                    ],
                                    [
                                        106.828153,
                                        -6.148367
                                    ],
                                    [
                                        106.828134,
                                        -6.148245
                                    ],
                                    [
                                        106.829456,
                                        -6.146222
                                    ],
                                    [
                                        106.831141,
                                        -6.140045
                                    ],
                                    [
                                        106.822163,
                                        -6.133491
                                    ],
                                    [
                                        106.821423,
                                        -6.133446
                                    ],
                                    [
                                        106.818237,
                                        -6.133404
                                    ],
                                    [
                                        106.810032,
                                        -6.132308
                                    ],
                                    [
                                        106.809105,
                                        -6.128829
                                    ]
                                ],
                                [
                                    [
                                        106.862566,
                                        -6.172418
                                    ],
                                    [
                                        106.862595,
                                        -6.172484
                                    ],
                                    [
                                        106.864274,
                                        -6.173321
                                    ],
                                    [
                                        106.86986,
                                        -6.178026
                                    ],
                                    [
                                        106.873742,
                                        -6.188108
                                    ],
                                    [
                                        106.875233,
                                        -6.189616
                                    ],
                                    [
                                        106.875503,
                                        -6.189624
                                    ],
                                    [
                                        106.876386,
                                        -6.18947
                                    ],
                                    [
                                        106.876486,
                                        -6.189396
                                    ],
                                    [
                                        106.887565,
                                        -6.189408
                                    ],
                                    [
                                        106.889465,
                                        -6.192156
                                    ],
                                    [
                                        106.891382,
                                        -6.192926
                                    ],
                                    [
                                        106.891628,
                                        -6.192909
                                    ],
                                    [
                                        106.893065,
                                        -6.192155
                                    ],
                                    [
                                        106.899433,
                                        -6.187094
                                    ],
                                    [
                                        106.910295,
                                        -6.183514
                                    ],
                                    [
                                        106.911784,
                                        -6.183972
                                    ],
                                    [
                                        106.911883,
                                        -6.183995
                                    ],
                                    [
                                        106.913598,
                                        -6.184306
                                    ],
                                    [
                                        106.913912,
                                        -6.184315
                                    ],
                                    [
                                        106.921016,
                                        -6.185404
                                    ],
                                    [
                                        106.925261,
                                        -6.18605
                                    ],
                                    [
                                        106.927146,
                                        -6.185292
                                    ],
                                    [
                                        106.927675,
                                        -6.184062
                                    ],
                                    [
                                        106.927839,
                                        -6.183566
                                    ],
                                    [
                                        106.927828,
                                        -6.183482
                                    ],
                                    [
                                        106.926595,
                                        -6.181734
                                    ],
                                    [
                                        106.924562,
                                        -6.170567
                                    ],
                                    [
                                        106.92649,
                                        -6.1659
                                    ],
                                    [
                                        106.926684,
                                        -6.165554
                                    ],
                                    [
                                        106.931347,
                                        -6.155805
                                    ],
                                    [
                                        106.926174,
                                        -6.145146
                                    ],
                                    [
                                        106.923748,
                                        -6.141526
                                    ],
                                    [
                                        106.919639,
                                        -6.132529
                                    ],
                                    [
                                        106.917974,
                                        -6.130894
                                    ],
                                    [
                                        106.917583,
                                        -6.130759
                                    ],
                                    [
                                        106.916479,
                                        -6.130804
                                    ],
                                    [
                                        106.916357,
                                        -6.131028
                                    ],
                                    [
                                        106.914582,
                                        -6.135945
                                    ],
                                    [
                                        106.906793,
                                        -6.142223
                                    ],
                                    [
                                        106.90135,
                                        -6.141305
                                    ],
                                    [
                                        106.895434,
                                        -6.134217
                                    ],
                                    [
                                        106.893915,
                                        -6.125807
                                    ],
                                    [
                                        106.894237,
                                        -6.123689
                                    ],
                                    [
                                        106.894664,
                                        -6.121313
                                    ],
                                    [
                                        106.894931,
                                        -6.119437
                                    ],
                                    [
                                        106.894934,
                                        -6.119233
                                    ],
                                    [
                                        106.893077,
                                        -6.117611
                                    ],
                                    [
                                        106.893029,
                                        -6.117613
                                    ],
                                    [
                                        106.891335,
                                        -6.119181
                                    ],
                                    [
                                        106.882511,
                                        -6.124583
                                    ],
                                    [
                                        106.881782,
                                        -6.128109
                                    ],
                                    [
                                        106.876987,
                                        -6.13568
                                    ],
                                    [
                                        106.871103,
                                        -6.135847
                                    ],
                                    [
                                        106.870632,
                                        -6.135933
                                    ],
                                    [
                                        106.867021,
                                        -6.145456
                                    ],
                                    [
                                        106.866313,
                                        -6.156831
                                    ],
                                    [
                                        106.865938,
                                        -6.157834
                                    ],
                                    [
                                        106.86623,
                                        -6.159311
                                    ],
                                    [
                                        106.863222,
                                        -6.170092
                                    ],
                                    [
                                        106.862566,
                                        -6.172418
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "1,087,684",
                            "age": {
                                "0": {
                                    "persen": 16.109079413105768,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 530746.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 15.840618025909404,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 521901.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 15.191727579683171,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 500522.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 15.026856776376146,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 495090.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 16.173334105778995,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 532863.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 18.089744731847766,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 596003.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 17.9940759593839,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 592851.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 15.954588914425214,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 525656.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 13.651011136849736,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 449760.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 16.42070101427536,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 541013.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 10.831878229492752,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 356878.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 8.15664305381445,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 268737.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 6.865812716214213,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 226208.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 3.4146952973589086,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 112504.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 3294701,
                                    "persen": 49.600707317598776,
                                    "total": 1634195
                                },
                                "male": {
                                    "from": 3294701,
                                    "persen": 50.39929268240122,
                                    "total": 1660506
                                },
                                "total": {
                                    "from": 3294701,
                                    "persen": 100.0,
                                    "total": 3294701
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 15.0,
                            "high": 0,
                            "kabupaten": "JAKARTA UTARA",
                            "kecamatan": "KELAPA GADING",
                            "ket": "Site 1",
                            "kodepodes": "3175050001",
                            "latitude": -683349.76,
                            "longitude": 11899557.621,
                            "low": 0,
                            "luas_m": 183360161340.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "KELAPA GADING BARAT",
                            "poi": {
                                "Apartment": {
                                    "kode_sub_kategori": "2601",
                                    "min_dist": 92.45990576,
                                    "tot": 38
                                },
                                "Bus Stop": {
                                    "kode_sub_kategori": "1110",
                                    "min_dist": 92.45990576,
                                    "tot": 104
                                },
                                "Office Building": {
                                    "kode_sub_kategori": "2603",
                                    "min_dist": 92.45990576,
                                    "tot": 17
                                },
                                "Senior High School": {
                                    "kode_sub_kategori": "1404",
                                    "min_dist": 92.45990576,
                                    "tot": 33
                                },
                                "Store": {
                                    "kode_sub_kategori": "1610",
                                    "min_dist": 92.45990576,
                                    "tot": 60
                                }
                            },
                            "provinsi": "DKI JAKARTA",
                            "ses": {
                                "high": 16.434000000000005,
                                "low": 26.979000000000013,
                                "medium_high": 37.84700000000001,
                                "medium_low": 18.719000000000005
                            },
                            "tipe_driving": "driving-car",
                            "zone": [
                                "CAMPURAN",
                                "INDUSTRI DAN PERDAGANGAN/JASA",
                                "KAWASAN LINDUNG",
                                "PARIWISATA",
                                "PELAYANAN UMUM",
                                "PEMERINTAHAN",
                                "PERMUKIMAN",
                                "RUANG TERBUKA"
                            ]
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            }
        },
        "point": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                106.90534200000005,
                                -6.17932390008002
                            ],
                            "type": "Point"
                        },
                        "id": "17",
                        "properties": {
                            "alamat_merchant": "Jalan Puskesmas No.61, RT.3/RW.6, 6, Kelapa Gading Timur",
                            "developer_name": null,
                            "dist": 2329.62085642,
                            "gid": 2228880,
                            "id_brand": 963,
                            "id_merchant": 1351862.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.17932390008,
                            "longitude": 106.905342,
                            "nama_brand": "DRP",
                            "nama_merchant": "Bismi Stuff",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90042999899995,
                                -6.16769000029
                            ],
                            "type": "Point"
                        },
                        "id": "18",
                        "properties": {
                            "alamat_merchant": "Jl. Boulevard Raya No. 12-16, Kelapa Gading, Jakarta Utara, Jakarta 14240",
                            "developer_name": null,
                            "dist": 994.6776218,
                            "gid": 2237365,
                            "id_brand": 963,
                            "id_merchant": 1360345.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.16769000029,
                            "longitude": 106.900429999,
                            "nama_brand": "DRP",
                            "nama_merchant": "Glodok Elektronik Boelevard Kelapa Gading",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.902061172,
                                -6.165205421689985
                            ],
                            "type": "Point"
                        },
                        "id": "20",
                        "properties": {
                            "alamat_merchant": "Jl Boulevard Raya, Kelapa Gading Timur, Kelapa Gading, Jakarta Utara, DKI Jakarta",
                            "developer_name": null,
                            "dist": 720.70129912,
                            "gid": 2239105,
                            "id_brand": 963,
                            "id_merchant": 1362083.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.16520542169,
                            "longitude": 106.902061172,
                            "nama_brand": "DRP",
                            "nama_merchant": "Ck",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90393,
                                -6.162520000200007
                            ],
                            "type": "Point"
                        },
                        "id": "21",
                        "properties": {
                            "alamat_merchant": "Jl Boulevard Raya, Kelapa Gading Timur, Kelapa Gading, Jakarta Utara, DKI Jakarta",
                            "developer_name": null,
                            "dist": 512.96136129,
                            "gid": 2241329,
                            "id_brand": 963,
                            "id_merchant": 1364307.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.1625200002,
                            "longitude": 106.90393,
                            "nama_brand": "DRP",
                            "nama_merchant": "Jakarta Fruit Market",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90654200000003,
                                -6.160950200290034
                            ],
                            "type": "Point"
                        },
                        "id": "22",
                        "properties": {
                            "alamat_merchant": "Jalan Boulevard Timur 57 13 18, Klp. Gading Tim., Klp. Gading, Kota Jkt Utara, Daerah Khusus Ibukota Jakarta 14240, Indonesia",
                            "developer_name": null,
                            "dist": 636.45968743,
                            "gid": 2242498,
                            "id_brand": 963,
                            "id_merchant": 1365476.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.16095020029,
                            "longitude": 106.906542,
                            "nama_brand": "DRP",
                            "nama_merchant": "Mega Makmur Lestari. PT",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90536100000001,
                                -6.158718299710038
                            ],
                            "type": "Point"
                        },
                        "id": "35",
                        "properties": {
                            "alamat_merchant": "JL. Boulevard Kelapa Gading, Blok RA 19 / 3, RT.1/RW.18, Klp. Gading Tim., Klp. Gading, Kota Jkt Utara, Daerah Khusus Ibukota Jakarta 14240, Indonesia",
                            "developer_name": null,
                            "dist": 458.37024059,
                            "gid": 2243798,
                            "id_brand": 963,
                            "id_merchant": 1366776.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.15871829971,
                            "longitude": 106.905361,
                            "nama_brand": "DRP",
                            "nama_merchant": "Blue Depo air minum",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90931700000004,
                                -6.14731869040996
                            ],
                            "type": "Point"
                        },
                        "id": "36",
                        "properties": {
                            "alamat_merchant": "Jl. Boulevard Raya Blok QJ1 No.6, RT.1/RW.12, Klp. Gading Bar., Klp. Gading, Kota Jkt Utara, Daerah Khusus Ibukota Jakarta 14240, Indonesia",
                            "developer_name": null,
                            "dist": 1557.59491887,
                            "gid": 2250668,
                            "id_brand": 963,
                            "id_merchant": 1373644.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.14731869041,
                            "longitude": 106.909317,
                            "nama_brand": "DRP",
                            "nama_merchant": "Sinar Terang Kencana",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.91008100000002,
                                -6.144458990189956
                            ],
                            "type": "Point"
                        },
                        "id": "37",
                        "properties": {
                            "alamat_merchant": "JL. Kelapa Hibrida I, Blok RA5, No. 2, Komplek Kelapa Gading Permai, RT.11/RW.15, Pegangsaan Dua, Klp. Gading, Kota Jkt Utara, Daerah Khusus Ibukota Jakarta 14240, Indonesia",
                            "developer_name": null,
                            "dist": 1869.78089102,
                            "gid": 2252218,
                            "id_brand": 963,
                            "id_merchant": 1375190.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.14445899019,
                            "longitude": 106.910081,
                            "nama_brand": "DRP",
                            "nama_merchant": "Mentari. UD",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.8965447,
                                -6.1737652
                            ],
                            "type": "Point"
                        },
                        "id": "41",
                        "properties": {
                            "alamat_merchant": "Jl. Boulevard Raya",
                            "developer_name": null,
                            "dist": 1744.57602437,
                            "gid": 3420170,
                            "id_brand": 986,
                            "id_merchant": 1800004.0,
                            "kode_brand": "2603001",
                            "kode_kategori": "26",
                            "kode_sub_kategori": "2603",
                            "latitude": -6.1737652,
                            "longitude": 106.8965447,
                            "nama_brand": "Summarecon (Office Building)",
                            "nama_merchant": "The Kensington Commercial",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": "",
                            "subclass": "Office Building"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90998,
                                -6.14271
                            ],
                            "type": "Point"
                        },
                        "id": "42",
                        "properties": {
                            "alamat_merchant": "Jl. Boulevard Pegangsaan Raya",
                            "developer_name": null,
                            "dist": 2032.60349909,
                            "gid": 3420158,
                            "id_brand": 980,
                            "id_merchant": 1900020.0,
                            "kode_brand": "1110001",
                            "kode_kategori": "11",
                            "kode_sub_kategori": "1110",
                            "latitude": -6.14271,
                            "longitude": 106.90998,
                            "nama_brand": "N/A (Bus Stop)",
                            "nama_merchant": "Bus Stop Taman Mandiri",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": "",
                            "subclass": "Bus Stop"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.90998,
                                -6.14271
                            ],
                            "type": "Point"
                        },
                        "id": "44",
                        "properties": {
                            "alamat_merchant": "Jl. Boulevard Pegangsaan Raya",
                            "developer_name": null,
                            "dist": 2032.60349909,
                            "gid": 3420158,
                            "id_brand": 980,
                            "id_merchant": 1900020.0,
                            "kode_brand": "1110001",
                            "kode_kategori": "11",
                            "kode_sub_kategori": "1110",
                            "latitude": -6.14271,
                            "longitude": 106.90998,
                            "nama_brand": "N/A BUS STOP",
                            "nama_merchant": "Bus Stop Taman Mandiri",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": "",
                            "subclass": "Bus Stop"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.874404468,
                                -6.176545343890001
                            ],
                            "type": "Point"
                        },
                        "id": "56",
                        "properties": {
                            "alamat_merchant": "Jl. Cempaka Putih Raya No 141, Cempaka Putih Timur, Cempaka Putih, Jakarta Pusat, DKI Jakarta 10510",
                            "developer_name": null,
                            "dist": 3562.01676782,
                            "gid": 2230900,
                            "id_brand": 963,
                            "id_merchant": 1353881.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.17654534389,
                            "longitude": 106.874404468,
                            "nama_brand": "DRP",
                            "nama_merchant": "Cempaka Buah",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            },
            "15": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                106.95417449900005,
                                -6.228551953410029
                            ],
                            "type": "Point"
                        },
                        "id": "0",
                        "properties": {
                            "alamat_merchant": "Jl Bintara Raya, Bintara, Bekasi Barat, Kota Bekasi, Jawa Barat",
                            "developer_name": null,
                            "dist": 9719.44388742,
                            "gid": 2192549,
                            "id_brand": 963,
                            "id_merchant": 1315543.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.22855195341,
                            "longitude": 106.954174499,
                            "nama_brand": "DRP",
                            "nama_merchant": "Idolmart",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.89488999899997,
                                -6.223219999800018
                            ],
                            "type": "Point"
                        },
                        "id": "1",
                        "properties": {
                            "alamat_merchant": "Jl Jend Basuki Rahmat, Pondok Bambu, Duren Sawit, Jakarta Timur, DKI Jakarta",
                            "developer_name": null,
                            "dist": 7199.58074561,
                            "gid": 2197083,
                            "id_brand": 963,
                            "id_merchant": 1320068.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.2232199998,
                            "longitude": 106.894889999,
                            "nama_brand": "DRP",
                            "nama_merchant": "Patra Mart",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.889682,
                                -6.198450600409973
                            ],
                            "type": "Point"
                        },
                        "id": "2",
                        "properties": {
                            "alamat_merchant": "Pasar Rawamangun, Jalan Pegambiran RT.9/RW.8, Rawamangun",
                            "developer_name": null,
                            "dist": 4591.8693159,
                            "gid": 2213957,
                            "id_brand": 963,
                            "id_merchant": 1336941.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19845060041,
                            "longitude": 106.889682,
                            "nama_brand": "DRP",
                            "nama_merchant": "Anantara",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88965499999999,
                                -6.198450200219958
                            ],
                            "type": "Point"
                        },
                        "id": "3",
                        "properties": {
                            "alamat_merchant": "Pasar Rawamangun, Jalan Pegambiran RT.9/RW.8, Rawamangun",
                            "developer_name": null,
                            "dist": 4592.65624865,
                            "gid": 2213958,
                            "id_brand": 963,
                            "id_merchant": 1336942.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19845020022,
                            "longitude": 106.889655,
                            "nama_brand": "DRP",
                            "nama_merchant": "Aruna",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.92893000000004,
                                -6.227270000410008
                            ],
                            "type": "Point"
                        },
                        "id": "4",
                        "properties": {
                            "alamat_merchant": "Jl Raya Nusa Indah, Malaka Sari, Duren Sawit, Jakarta Timur, DKI Jakarta",
                            "developer_name": null,
                            "dist": 8209.03656899,
                            "gid": 2193615,
                            "id_brand": 963,
                            "id_merchant": 1316600.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.22727000041,
                            "longitude": 106.92893,
                            "nama_brand": "DRP",
                            "nama_merchant": "Idolmart",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88978899999998,
                                -6.198484600179994
                            ],
                            "type": "Point"
                        },
                        "id": "5",
                        "properties": {
                            "alamat_merchant": "Pasar Rawamangun, Jalan Pegambiran RT.9/RW.8, Rawamangun",
                            "developer_name": null,
                            "dist": 4592.23360839,
                            "gid": 2213936,
                            "id_brand": 963,
                            "id_merchant": 1336922.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19848460018,
                            "longitude": 106.889789,
                            "nama_brand": "DRP",
                            "nama_merchant": "Putri Santika",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88978999999996,
                                -6.198456599789988
                            ],
                            "type": "Point"
                        },
                        "id": "6",
                        "properties": {
                            "alamat_merchant": "Pasar Rawamangun, Jalan Pegambiran RT.9/RW.8, Rawamangun",
                            "developer_name": null,
                            "dist": 4589.20986749,
                            "gid": 2213953,
                            "id_brand": 963,
                            "id_merchant": 1336939.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19845659979,
                            "longitude": 106.88979,
                            "nama_brand": "DRP",
                            "nama_merchant": "Napitu",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88951600000003,
                                -6.1983190997500115
                            ],
                            "type": "Point"
                        },
                        "id": "7",
                        "properties": {
                            "alamat_merchant": "Pasar Rawamangun, Jalan Pegambiran RT.9/RW.8, Rawamangun",
                            "developer_name": null,
                            "dist": 4582.96888813,
                            "gid": 2214043,
                            "id_brand": 963,
                            "id_merchant": 1337027.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19831909975,
                            "longitude": 106.889516,
                            "nama_brand": "DRP",
                            "nama_merchant": "Servio",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.89130000000003,
                                -6.196719999929985
                            ],
                            "type": "Point"
                        },
                        "id": "8",
                        "properties": {
                            "alamat_merchant": "Jl Sunan Sedayu, Jati, Pulogadung, Jakarta Timur, DKI Jakarta",
                            "developer_name": null,
                            "dist": 4358.94540644,
                            "gid": 2215443,
                            "id_brand": 963,
                            "id_merchant": 1338426.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19671999993,
                            "longitude": 106.8913,
                            "nama_brand": "DRP",
                            "nama_merchant": "Soho",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.87090000000002,
                                -6.196260000300042
                            ],
                            "type": "Point"
                        },
                        "id": "9",
                        "properties": {
                            "alamat_merchant": "Jl Utam Kayu Raya, Utan Kayu Utara, Matraman, Jakarta Timur, DKI Jakarta",
                            "developer_name": null,
                            "dist": 5348.02762106,
                            "gid": 2215816,
                            "id_brand": 963,
                            "id_merchant": 1338799.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.1962600003,
                            "longitude": 106.8709,
                            "nama_brand": "DRP",
                            "nama_merchant": "Ikhtiar Mm",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88244200000004,
                                -6.196083000229975
                            ],
                            "type": "Point"
                        },
                        "id": "10",
                        "properties": {
                            "alamat_merchant": "Pasar Sunan Giri, Jalan Sunan Giri RT.8/RW.15, Rawamangun",
                            "developer_name": null,
                            "dist": 4638.26003454,
                            "gid": 2215932,
                            "id_brand": 963,
                            "id_merchant": 1338914.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19608300023,
                            "longitude": 106.882442,
                            "nama_brand": "DRP",
                            "nama_merchant": "Indra",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                106.88246799899997,
                                -6.1960605999200125
                            ],
                            "type": "Point"
                        },
                        "id": "11",
                        "properties": {
                            "alamat_merchant": "Pasar Sunan Giri, Jalan Sunan Giri RT.8/RW.15, Rawamangun",
                            "developer_name": null,
                            "dist": 4634.74668929,
                            "gid": 2215943,
                            "id_brand": 963,
                            "id_merchant": 1338925.0,
                            "kode_brand": "1610004",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.19606059992,
                            "longitude": 106.882467999,
                            "nama_brand": "DRP",
                            "nama_merchant": "Arita",
                            "number_of_parking": null,
                            "parking_fees": null,
                            "phone_merchant": null,
                            "subclass": "Store"
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            }
        }
    }
}
```

</details>
