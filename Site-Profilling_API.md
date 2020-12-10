# API Site Profilling

#### Postman
<a href="site-profilling.postman_collection.json" download>Download Postman Collection</a>

#### API Swagger
<a href="https://siteprofillingclient.lokasiintelligence.com/api/doc" download>API Documentation Swagger</a>

## HTTP Request Login
```URL
POST https://authclient.lokasiintelligence.com/users/login
```
#### Header

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| client_id   | required	  	|  `431322697`	   |
| client_secret  | required	  	|  `U2FsdGVkX19cQ7QtXcaKmNAUxPltu1ct/e2li65h64aNEfPCXsIwJo+Tg48NNAIh2LF+binkHw9HHsjTntgoYvlPzSlOthlUKawuX6xYWM9ptUKeL0xmR3kwtUDvjSSN`  	   |

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
curl --location --request POST 'http://authclient.lokasiintelligence.com/users/login' \
--header 'Content-Type: application/json' \
--header 'client_id: 431322697' \
--header 'client_secret: U2FsdGVkX19cQ7QtXcaKmNAUxPltu1ct/e2li65h64aNEfPCXsIwJo+Tg48NNAIh2LF+binkHw9HHsjTntgoYvlPzSlOthlUKawuX6xYWM9ptUKeL0xmR3kwtUDvjSSN' \
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
POST https://siteprofillingclient.lokasiintelligence.com/api/v1.0/drivetime
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
|informal|provinsi|berisi informasi provinsi|
||kab_kot|berisi informasi kabupaten/kota|
||kecamtan|berisi informasi kecamatan|
||informal|berisi informasi area informal dibawah kecamatan|
||polygon|berisi geojson koordinat batas informal|
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
curl --location --request POST 'https://siteprofillingclient.lokasiintelligence.com/api/v1.0/drivetime' \
--header 'client_id: 431322697' \
--header 'client_secret: U2FsdGVkX19cQ7QtXcaKmNAUxPltu1ct/e2li65h64aNEfPCXsIwJo+Tg48NNAIh2LF+binkHw9HHsjTntgoYvlPzSlOthlUKawuX6xYWM9ptUKeL0xmR3kwtUDvjSSN' \
--header 'Authorization: $AUTHORIZATION' \
--header 'Content-Type: application/json' \
--data-raw '{
    "coordinate": [
        {
            "name": "Gading Serpong",
            "coordinate": [
               106.628007,-6.246553
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
    "Gading Serpong": {
        "area": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.60447,
                                        -6.258654
                                    ],
                                    [
                                        106.605525,
                                        -6.25099
                                    ],
                                    [
                                        106.605566,
                                        -6.250803
```

</summary>

```json


{
    "Gading Serpong": {
        "area": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.60447,
                                        -6.258654
                                    ],
                                    [
                                        106.605525,
                                        -6.25099
                                    ],
                                    [
                                        106.605566,
                                        -6.250803
                                    ],
                                    [
                                        106.607563,
                                        -6.242254
                                    ],
                                    [
                                        106.60895,
                                        -6.234161
                                    ],
                                    [
                                        106.613268,
                                        -6.226371
                                    ],
                                    [
                                        106.614234,
                                        -6.225935
                                    ],
                                    [
                                        106.615989,
                                        -6.225967
                                    ],
                                    [
                                        106.616326,
                                        -6.226006
                                    ],
                                    [
                                        106.61782,
                                        -6.226254
                                    ],
                                    [
                                        106.624152,
                                        -6.22909
                                    ],
                                    [
                                        106.62439,
                                        -6.229074
                                    ],
                                    [
                                        106.630175,
                                        -6.218563
                                    ],
                                    [
                                        106.630389,
                                        -6.217494
                                    ],
                                    [
                                        106.630582,
                                        -6.216239
                                    ],
                                    [
                                        106.630736,
                                        -6.216136
                                    ],
                                    [
                                        106.632952,
                                        -6.216272
                                    ],
                                    [
                                        106.633037,
                                        -6.216375
                                    ],
                                    [
                                        106.639518,
                                        -6.225113
                                    ],
                                    [
                                        106.640089,
                                        -6.230711
                                    ],
                                    [
                                        106.643074,
                                        -6.242228
                                    ],
                                    [
                                        106.644864,
                                        -6.244708
                                    ],
                                    [
                                        106.645981,
                                        -6.249904
                                    ],
                                    [
                                        106.647137,
                                        -6.259356
                                    ],
                                    [
                                        106.647189,
                                        -6.260136
                                    ],
                                    [
                                        106.645797,
                                        -6.271642
                                    ],
                                    [
                                        106.644787,
                                        -6.272131
                                    ],
                                    [
                                        106.644726,
                                        -6.272159
                                    ],
                                    [
                                        106.63533,
                                        -6.275316
                                    ],
                                    [
                                        106.632782,
                                        -6.276809
                                    ],
                                    [
                                        106.632293,
                                        -6.276081
                                    ],
                                    [
                                        106.628816,
                                        -6.270714
                                    ],
                                    [
                                        106.620435,
                                        -6.26988
                                    ],
                                    [
                                        106.618207,
                                        -6.270885
                                    ],
                                    [
                                        106.616797,
                                        -6.270683
                                    ],
                                    [
                                        106.614677,
                                        -6.270178
                                    ],
                                    [
                                        106.615007,
                                        -6.26853
                                    ],
                                    [
                                        106.606156,
                                        -6.260761
                                    ],
                                    [
                                        106.605748,
                                        -6.260634
                                    ],
                                    [
                                        106.605654,
                                        -6.260584
                                    ],
                                    [
                                        106.60447,
                                        -6.258654
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "25,948",
                            "age": {
                                "0": {
                                    "persen": 15.212101371471071,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 12124.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 17.003826937163968,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13552.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 16.82816756797839,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13412.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 17.52327678604132,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13966.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 17.391532259152136,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13861.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 17.937331013407327,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 14296.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 18.89718399502852,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 15061.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 18.125537480391873,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 14446.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 14.535812800106596,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 11585.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 17.304957284339245,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13792.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 9.33629547221348,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 7441.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 5.815579829822535,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 4635.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 4.327494030864709,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 3449.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 2.0087903576150765,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 1601.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 79700,
                                    "persen": 49.19447929736512,
                                    "total": 39208
                                },
                                "male": {
                                    "from": 79700,
                                    "persen": 50.80552070263488,
                                    "total": 40492
                                },
                                "total": {
                                    "from": 678284,
                                    "persen": 11.750240312317555,
                                    "total": 79700
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 10.0,
                            "high": 0,
                            "kabupaten": "TANGERANG",
                            "kecamatan": "KELAPA DUA",
                            "ket": "Gading Serpong",
                            "kodepodes": "3603051002",
                            "latitude": -692364.116,
                            "longitude": 11869664.984,
                            "low": 0,
                            "luas_m": 21129435130.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "CURUG SANGERENG",
                            "provinsi": "BANTEN",
                            "ses": {
                                "high": 75.655,
                                "low": 0,
                                "medium_high": 20.412,
                                "medium_low": 3.933
                            },
                            "tipe_driving": "driving-car",
                            "zone": [
                                "DATA BELUM TERSEDIA"
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
                                        106.559254,
                                        -6.220331
                                    ],
                                    [
                                        106.560485,
                                        -6.216948
                                    ],
                                    [
                                        106.562684,
                                        -6.217748
                                    ],
                                    [
                                        106.567775,
                                        -6.219121
                                    ],
                                    [
                                        106.575179,
                                        -6.219864
                                    ],
                                    [
                                        106.586749,
                                        -6.222447
                                    ],
                                    [
                                        106.587174,
                                        -6.222281
                                    ],
                                    [
                                        106.594856,
                                        -6.216075
                                    ],
                                    [
                                        106.598265,
                                        -6.212234
                                    ],
                                    [
                                        106.598529,
                                        -6.204077
                                    ],
                                    [
                                        106.598567,
                                        -6.203687
                                    ],
                                    [
                                        106.598609,
                                        -6.203273
                                    ],
                                    [
                                        106.598685,
                                        -6.202463
                                    ],
                                    [
                                        106.600463,
                                        -6.20201
                                    ],
                                    [
                                        106.601955,
                                        -6.201549
                                    ],
                                    [
                                        106.604564,
                                        -6.200516
                                    ],
                                    [
                                        106.609412,
                                        -6.189723
                                    ],
                                    [
                                        106.609413,
                                        -6.189691
                                    ],
                                    [
                                        106.609414,
                                        -6.189663
                                    ],
                                    [
                                        106.609416,
                                        -6.18963
                                    ],
                                    [
                                        106.611382,
                                        -6.184979
                                    ],
                                    [
                                        106.612906,
                                        -6.183567
                                    ],
                                    [
                                        106.621061,
                                        -6.18038
                                    ],
                                    [
                                        106.623743,
                                        -6.176726
                                    ],
                                    [
                                        106.623953,
                                        -6.176635
                                    ],
                                    [
                                        106.62818,
                                        -6.175788
                                    ],
                                    [
                                        106.635083,
                                        -6.175596
                                    ],
                                    [
                                        106.637997,
                                        -6.176168
                                    ],
                                    [
                                        106.645453,
                                        -6.180708
                                    ],
                                    [
                                        106.64762,
                                        -6.182825
                                    ],
                                    [
                                        106.647157,
                                        -6.187436
                                    ],
                                    [
                                        106.647024,
                                        -6.187848
                                    ],
                                    [
                                        106.645877,
                                        -6.197808
                                    ],
                                    [
                                        106.644537,
                                        -6.202196
                                    ],
                                    [
                                        106.649484,
                                        -6.212868
                                    ],
                                    [
                                        106.659641,
                                        -6.217165
                                    ],
                                    [
                                        106.663693,
                                        -6.216216
                                    ],
                                    [
                                        106.668504,
                                        -6.214803
                                    ],
                                    [
                                        106.672592,
                                        -6.214407
                                    ],
                                    [
                                        106.680109,
                                        -6.212291
                                    ],
                                    [
                                        106.686828,
                                        -6.210436
                                    ],
                                    [
                                        106.691967,
                                        -6.208982
                                    ],
                                    [
                                        106.69973,
                                        -6.204658
                                    ],
                                    [
                                        106.701971,
                                        -6.207476
                                    ],
                                    [
                                        106.70124,
                                        -6.208056
                                    ],
                                    [
                                        106.699446,
                                        -6.209376
                                    ],
                                    [
                                        106.693093,
                                        -6.212402
                                    ],
                                    [
                                        106.687809,
                                        -6.2139
                                    ],
                                    [
                                        106.68099,
                                        -6.215782
                                    ],
                                    [
                                        106.67481,
                                        -6.223983
                                    ],
                                    [
                                        106.674322,
                                        -6.229451
                                    ],
                                    [
                                        106.674861,
                                        -6.233131
                                    ],
                                    [
                                        106.673367,
                                        -6.23651
                                    ],
                                    [
                                        106.672063,
                                        -6.23946
                                    ],
                                    [
                                        106.671357,
                                        -6.240986
                                    ],
                                    [
                                        106.661847,
                                        -6.245863
                                    ],
                                    [
                                        106.661216,
                                        -6.249799
                                    ],
                                    [
                                        106.660982,
                                        -6.250171
                                    ],
                                    [
                                        106.657183,
                                        -6.259646
                                    ],
                                    [
                                        106.657094,
                                        -6.262209
                                    ],
                                    [
                                        106.657056,
                                        -6.262552
                                    ],
                                    [
                                        106.656726,
                                        -6.26686
                                    ],
                                    [
                                        106.659335,
                                        -6.274176
                                    ],
                                    [
                                        106.663607,
                                        -6.277729
                                    ],
                                    [
                                        106.663662,
                                        -6.277776
                                    ],
                                    [
                                        106.664635,
                                        -6.278988
                                    ],
                                    [
                                        106.666512,
                                        -6.282105
                                    ],
                                    [
                                        106.665897,
                                        -6.283421
                                    ],
                                    [
                                        106.6647,
                                        -6.285216
                                    ],
                                    [
                                        106.664377,
                                        -6.285028
                                    ],
                                    [
                                        106.657113,
                                        -6.284568
                                    ],
                                    [
                                        106.653431,
                                        -6.291243
                                    ],
                                    [
                                        106.657152,
                                        -6.296692
                                    ],
                                    [
                                        106.664089,
                                        -6.297826
                                    ],
                                    [
                                        106.664337,
                                        -6.29782
                                    ],
                                    [
                                        106.665784,
                                        -6.299281
                                    ],
                                    [
                                        106.665644,
                                        -6.300467
                                    ],
                                    [
                                        106.66556,
                                        -6.300699
                                    ],
                                    [
                                        106.664433,
                                        -6.301418
                                    ],
                                    [
                                        106.663878,
                                        -6.301657
                                    ],
                                    [
                                        106.656506,
                                        -6.307201
                                    ],
                                    [
                                        106.655195,
                                        -6.311763
                                    ],
                                    [
                                        106.647933,
                                        -6.319504
                                    ],
                                    [
                                        106.643508,
                                        -6.32181
                                    ],
                                    [
                                        106.641986,
                                        -6.320858
                                    ],
                                    [
                                        106.640482,
                                        -6.31986
                                    ],
                                    [
                                        106.639552,
                                        -6.311926
                                    ],
                                    [
                                        106.631567,
                                        -6.310345
                                    ],
                                    [
                                        106.630308,
                                        -6.310365
                                    ],
                                    [
                                        106.629754,
                                        -6.310273
                                    ],
                                    [
                                        106.630344,
                                        -6.306722
                                    ],
                                    [
                                        106.621498,
                                        -6.30052
                                    ],
                                    [
                                        106.621496,
                                        -6.30052
                                    ],
                                    [
                                        106.619629,
                                        -6.29931
                                    ],
                                    [
                                        106.619619,
                                        -6.298755
                                    ],
                                    [
                                        106.616567,
                                        -6.290512
                                    ],
                                    [
                                        106.616568,
                                        -6.290429
                                    ],
                                    [
                                        106.613749,
                                        -6.28225
                                    ],
                                    [
                                        106.604193,
                                        -6.287048
                                    ],
                                    [
                                        106.603972,
                                        -6.28735
                                    ],
                                    [
                                        106.597658,
                                        -6.293562
                                    ],
                                    [
                                        106.596398,
                                        -6.296612
                                    ],
                                    [
                                        106.596376,
                                        -6.296662
                                    ],
                                    [
                                        106.592978,
                                        -6.303744
                                    ],
                                    [
                                        106.592034,
                                        -6.305232
                                    ],
                                    [
                                        106.591769,
                                        -6.305331
                                    ],
                                    [
                                        106.59176,
                                        -6.305335
                                    ],
                                    [
                                        106.591394,
                                        -6.30547
                                    ],
                                    [
                                        106.585741,
                                        -6.302543
                                    ],
                                    [
                                        106.584829,
                                        -6.300264
                                    ],
                                    [
                                        106.584187,
                                        -6.296899
                                    ],
                                    [
                                        106.584186,
                                        -6.296878
                                    ],
                                    [
                                        106.584761,
                                        -6.296335
                                    ],
                                    [
                                        106.588368,
                                        -6.287795
                                    ],
                                    [
                                        106.5878,
                                        -6.284005
                                    ],
                                    [
                                        106.587782,
                                        -6.283397
                                    ],
                                    [
                                        106.587949,
                                        -6.282431
                                    ],
                                    [
                                        106.589052,
                                        -6.278524
                                    ],
                                    [
                                        106.586136,
                                        -6.267972
                                    ],
                                    [
                                        106.581807,
                                        -6.262813
                                    ],
                                    [
                                        106.57569,
                                        -6.260089
                                    ],
                                    [
                                        106.575636,
                                        -6.260065
                                    ],
                                    [
                                        106.574824,
                                        -6.257663
                                    ],
                                    [
                                        106.574912,
                                        -6.257481
                                    ],
                                    [
                                        106.577137,
                                        -6.256793
                                    ],
                                    [
                                        106.577191,
                                        -6.256817
                                    ],
                                    [
                                        106.580958,
                                        -6.258169
                                    ],
                                    [
                                        106.58769,
                                        -6.257526
                                    ],
                                    [
                                        106.589883,
                                        -6.25615
                                    ],
                                    [
                                        106.594244,
                                        -6.251778
                                    ],
                                    [
                                        106.596367,
                                        -6.248359
                                    ],
                                    [
                                        106.595537,
                                        -6.23764
                                    ],
                                    [
                                        106.589747,
                                        -6.236779
                                    ],
                                    [
                                        106.587365,
                                        -6.237528
                                    ],
                                    [
                                        106.584733,
                                        -6.23903
                                    ],
                                    [
                                        106.582704,
                                        -6.239294
                                    ],
                                    [
                                        106.58218,
                                        -6.239234
                                    ],
                                    [
                                        106.582119,
                                        -6.239174
                                    ],
                                    [
                                        106.581614,
                                        -6.237233
                                    ],
                                    [
                                        106.582372,
                                        -6.235461
                                    ],
                                    [
                                        106.583019,
                                        -6.234714
                                    ],
                                    [
                                        106.585321,
                                        -6.229386
                                    ],
                                    [
                                        106.585324,
                                        -6.229343
                                    ],
                                    [
                                        106.585325,
                                        -6.229335
                                    ],
                                    [
                                        106.585328,
                                        -6.229293
                                    ],
                                    [
                                        106.586732,
                                        -6.224733
                                    ],
                                    [
                                        106.574837,
                                        -6.223447
                                    ],
                                    [
                                        106.570726,
                                        -6.222689
                                    ],
                                    [
                                        106.561453,
                                        -6.221131
                                    ],
                                    [
                                        106.559254,
                                        -6.220331
                                    ]
                                ],
                                [
                                    [
                                        106.60447,
                                        -6.258654
                                    ],
                                    [
                                        106.605654,
                                        -6.260584
                                    ],
                                    [
                                        106.605748,
                                        -6.260634
                                    ],
                                    [
                                        106.606156,
                                        -6.260761
                                    ],
                                    [
                                        106.615007,
                                        -6.26853
                                    ],
                                    [
                                        106.614677,
                                        -6.270178
                                    ],
                                    [
                                        106.616797,
                                        -6.270683
                                    ],
                                    [
                                        106.618207,
                                        -6.270885
                                    ],
                                    [
                                        106.620435,
                                        -6.26988
                                    ],
                                    [
                                        106.628816,
                                        -6.270714
                                    ],
                                    [
                                        106.632293,
                                        -6.276081
                                    ],
                                    [
                                        106.632782,
                                        -6.276809
                                    ],
                                    [
                                        106.63533,
                                        -6.275316
                                    ],
                                    [
                                        106.644726,
                                        -6.272159
                                    ],
                                    [
                                        106.644787,
                                        -6.272131
                                    ],
                                    [
                                        106.645797,
                                        -6.271642
                                    ],
                                    [
                                        106.647189,
                                        -6.260136
                                    ],
                                    [
                                        106.647137,
                                        -6.259356
                                    ],
                                    [
                                        106.645981,
                                        -6.249904
                                    ],
                                    [
                                        106.644864,
                                        -6.244708
                                    ],
                                    [
                                        106.643074,
                                        -6.242228
                                    ],
                                    [
                                        106.640089,
                                        -6.230711
                                    ],
                                    [
                                        106.639518,
                                        -6.225113
                                    ],
                                    [
                                        106.633037,
                                        -6.216375
                                    ],
                                    [
                                        106.632952,
                                        -6.216272
                                    ],
                                    [
                                        106.630736,
                                        -6.216136
                                    ],
                                    [
                                        106.630582,
                                        -6.216239
                                    ],
                                    [
                                        106.630389,
                                        -6.217494
                                    ],
                                    [
                                        106.630175,
                                        -6.218563
                                    ],
                                    [
                                        106.62439,
                                        -6.229074
                                    ],
                                    [
                                        106.624152,
                                        -6.22909
                                    ],
                                    [
                                        106.61782,
                                        -6.226254
                                    ],
                                    [
                                        106.616326,
                                        -6.226006
                                    ],
                                    [
                                        106.615989,
                                        -6.225967
                                    ],
                                    [
                                        106.614234,
                                        -6.225935
                                    ],
                                    [
                                        106.613268,
                                        -6.226371
                                    ],
                                    [
                                        106.60895,
                                        -6.234161
                                    ],
                                    [
                                        106.607563,
                                        -6.242254
                                    ],
                                    [
                                        106.605566,
                                        -6.250803
                                    ],
                                    [
                                        106.605525,
                                        -6.25099
                                    ],
                                    [
                                        106.60447,
                                        -6.258654
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "223,714",
                            "age": {
                                "0": {
                                    "persen": 15.374385804710574,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 104282.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 15.805178801789307,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 107204.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 15.915014798648874,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 107949.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 17.340229002194423,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 117616.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 18.011481745418063,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 122169.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 18.636883488610387,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 126411.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 18.523066858307587,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 125639.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 16.516680172050073,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 112030.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 13.53651260088324,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 91816.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 16.292880114019436,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 110512.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 9.99772946984943,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 67813.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 7.117077734763414,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 48274.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 5.5485607272614885,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 37635.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 2.5863797220233367,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 17543.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 678284,
                                    "persen": 49.479126737472804,
                                    "total": 335609
                                },
                                "male": {
                                    "from": 678284,
                                    "persen": 50.520873262527196,
                                    "total": 342675
                                },
                                "total": {
                                    "from": 678284,
                                    "persen": 100.0,
                                    "total": 678284
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 15.0,
                            "high": 0,
                            "kabupaten": "TANGERANG",
                            "kecamatan": "KELAPA DUA",
                            "ket": "Gading Serpong",
                            "kodepodes": "3603051002",
                            "latitude": -692079.361,
                            "longitude": 11869767.295,
                            "low": 0,
                            "luas_m": 103961906530.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "CURUG SANGERENG",
                            "poi": {
                                "Store": {
                                    "kode_sub_kategori": "1610",
                                    "min_dist": 2038.42191309,
                                    "tot": 41
                                }
                            },
                            "provinsi": "BANTEN",
                            "ses": {
                                "high": 36.348,
                                "low": 4.832,
                                "medium_high": 22.845999999999997,
                                "medium_low": 35.977
                            },
                            "tipe_driving": "driving-car",
                            "zone": [
                                "DATA BELUM TERSEDIA"
                            ]
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            }
        },
        "informal": {
            "informal": [
                "CBD Karawaci A",
                "CBD Gading Serpong"
            ],
            "kab_kot": "TANGERANG",
            "kecamatan": "KELAPA DUA",
            "polygon": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        [
                                            106.60916719990661,
                                            -6.229383200374286
                                        ],
                                        [
                                            106.60801737979835,
                                            -6.231839873011666
                                        ],
                                        [
                                            106.60767180630887,
                                            -6.231677899715237
                                        ],
                                        [
                                            106.60626975514515,
                                            -6.2310619873208
                                        ],
                                        [
                                            106.60615973658275,
                                            -6.231010686394029
                                        ],
                                        [
                                            106.6060521228074,
                                            -6.230954509343064
                                        ],
                                        [
                                            106.60352721051237,
                                            -6.22956359988018
                                        ],
                                        [
                                            106.60324426401161,
                                            -6.229422951308095
                                        ],
                                        [
                                            106.60318106235633,
                                            -6.229397479809791
                                        ],
                                        [
                                            106.60317466907594,
                                            -6.229396209067772
                                        ],
                                        [
                                            106.60271086171701,
                                            -6.229327914551504
                                        ],
                                        [
                                            106.60201862745777,
                                            -6.229251387641398
                                        ],
                                        [
                                            106.60069861604848,
                                            -6.229136846388258
                                        ],
                                        [
                                            106.60093280040854,
                                            -6.226434200178176
                                        ],
                                        [
                                            106.60116698117133,
                                            -6.22373155306866
                                        ],
                                        [
                                            106.60251877462184,
                                            -6.22384885254246
                                        ],
                                        [
                                            106.60258225686584,
                                            -6.223855115421202
                                        ],
                                        [
                                            106.60335475291959,
                                            -6.223940515042614
                                        ],
                                        [
                                            106.6034517241178,
                                            -6.22395301022317
                                        ],
                                        [
                                            106.60403102061531,
                                            -6.224038309120601
                                        ],
                                        [
                                            106.60410712844134,
                                            -6.224050625336019
                                        ],
                                        [
                                            106.60416465087792,
                                            -6.224061417200573
                                        ],
                                        [
                                            106.60448654971458,
                                            -6.224125416554671
                                        ],
                                        [
                                            106.60458780258517,
                                            -6.224147569554646
                                        ],
                                        [
                                            106.60468813544918,
                                            -6.224173578847513
                                        ],
                                        [
                                            106.60478740081805,
                                            -6.224203407561106
                                        ],
                                        [
                                            106.6048854547999,
                                            -6.224237012528022
                                        ],
                                        [
                                            106.60497099381644,
                                            -6.224269817098275
                                        ],
                                        [
                                            106.60536799233921,
                                            -6.224429816382838
                                        ],
                                        [
                                            106.60546547345291,
                                            -6.224471336283102
                                        ],
                                        [
                                            106.60556125934465,
                                            -6.224516636933174
                                        ],
                                        [
                                            106.60599035826851,
                                            -6.22472993633744
                                        ],
                                        [
                                            106.60609167319222,
                                            -6.22478299364019
                                        ],
                                        [
                                            106.60856025285364,
                                            -6.226142867499277
                                        ],
                                        [
                                            106.6098813290601,
                                            -6.226723207210171
                                        ],
                                        [
                                            106.60994151079223,
                                            -6.226750525016655
                                        ],
                                        [
                                            106.61031700922263,
                                            -6.226926524139742
                                        ],
                                        [
                                            106.60916719990661,
                                            -6.229383200374286
                                        ]
                                    ]
                                ]
                            ],
                            "type": "MultiPolygon"
                        },
                        "id": "41",
                        "properties": {
                            "ALAMAT": "Jl. Jenderal Sudirman",
                            "DESA": "KELAPA DUA",
                            "KABKOT": "TANGERANG",
                            "KECAMATAN": "KELAPA DUA",
                            "NAMA": "CBD Karawaci A",
                            "PROVINSI": "BANTEN"
                        },
                        "type": "Feature"
                    },
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        [
                                            106.63227389042777,
                                            -6.226384583681465
                                        ],
                                        [
                                            106.63480358632978,
                                            -6.227359584297687
                                        ],
                                        [
                                            106.63733329099864,
                                            -6.228334572882147
                                        ],
                                        [
                                            106.63691642285471,
                                            -6.229417740636052
                                        ],
                                        [
                                            106.63579827956704,
                                            -6.232629667525032
                                        ],
                                        [
                                            106.63578569445434,
                                            -6.232665029767247
                                        ],
                                        [
                                            106.63577094197547,
                                            -6.232704629614886
                                        ],
                                        [
                                            106.63446262804791,
                                            -6.236134545872574
                                        ],
                                        [
                                            106.63318334603457,
                                            -6.23975670480803
                                        ],
                                        [
                                            106.63317480337452,
                                            -6.239780536842261
                                        ],
                                        [
                                            106.63314600708276,
                                            -6.239856179718856
                                        ],
                                        [
                                            106.63263491786734,
                                            -6.241140765933551
                                        ],
                                        [
                                            106.63259700514783,
                                            -6.241231259314986
                                        ],
                                        [
                                            106.63255584677495,
                                            -6.241320320975944
                                        ],
                                        [
                                            106.63251149670839,
                                            -6.241407834903612
                                        ],
                                        [
                                            106.63246401250427,
                                            -6.241493686884098
                                        ],
                                        [
                                            106.63240265445904,
                                            -6.24159487230537
                                        ],
                                        [
                                            106.63233694369507,
                                            -6.241693284217661
                                        ],
                                        [
                                            106.63226700611756,
                                            -6.24178873376303
                                        ],
                                        [
                                            106.63219297482607,
                                            -6.241881040177702
                                        ],
                                        [
                                            106.63210503911637,
                                            -6.241980835247318
                                        ],
                                        [
                                            106.63201991378804,
                                            -6.242068386047094
                                        ],
                                        [
                                            106.63201932203418,
                                            -6.242075522167568
                                        ],
                                        [
                                            106.63200620002618,
                                            -6.242199279672889
                                        ],
                                        [
                                            106.63198741948389,
                                            -6.242322303331605
                                        ],
                                        [
                                            106.63196707951721,
                                            -6.24242590792926
                                        ],
                                        [
                                            106.63194272587617,
                                            -6.242528641083823
                                        ],
                                        [
                                            106.6316242975235,
                                            -6.243764318568424
                                        ],
                                        [
                                            106.63158851889506,
                                            -6.243890466471782
                                        ],
                                        [
                                            106.63154668962812,
                                            -6.244014737490033
                                        ],
                                        [
                                            106.63149943025462,
                                            -6.244135596480419
                                        ],
                                        [
                                            106.63144644849484,
                                            -6.244254056079797
                                        ],
                                        [
                                            106.63127480568784,
                                            -6.244614444101273
                                        ],
                                        [
                                            106.6312269383726,
                                            -6.244710048329978
                                        ],
                                        [
                                            106.63117534336749,
                                            -6.244803691137349
                                        ],
                                        [
                                            106.63110845449177,
                                            -6.244913528036818
                                        ],
                                        [
                                            106.63075731060144,
                                            -6.245460516389585
                                        ],
                                        [
                                            106.63071765859314,
                                            -6.245520518257251
                                        ],
                                        [
                                            106.63067643097258,
                                            -6.245579447233581
                                        ],
                                        [
                                            106.62966272235684,
                                            -6.246988255003942
                                        ],
                                        [
                                            106.62964582679348,
                                            -6.247011476398427
                                        ],
                                        [
                                            106.62907301081094,
                                            -6.247790027587655
                                        ],
                                        [
                                            106.62870250451704,
                                            -6.248347042481953
                                        ],
                                        [
                                            106.62865603205029,
                                            -6.248536267934242
                                        ],
                                        [
                                            106.62835009168356,
                                            -6.250162744914689
                                        ],
                                        [
                                            106.62832744945234,
                                            -6.250270943249348
                                        ],
                                        [
                                            106.62830042032817,
                                            -6.250378128947432
                                        ],
                                        [
                                            106.6282690501767,
                                            -6.250484123043805
                                        ],
                                        [
                                            106.62823339025886,
                                            -6.250588750170664
                                        ],
                                        [
                                            106.6282206162885,
                                            -6.250623145641612
                                        ],
                                        [
                                            106.62795856373674,
                                            -6.251314385250623
                                        ],
                                        [
                                            106.62791019190189,
                                            -6.251433403328861
                                        ],
                                        [
                                            106.62757899857206,
                                            -6.252196018531379
                                        ],
                                        [
                                            106.62754730286588,
                                            -6.252266256482471
                                        ],
                                        [
                                            106.62751362595327,
                                            -6.252335563635313
                                        ],
                                        [
                                            106.62747799481377,
                                            -6.252403886030493
                                        ],
                                        [
                                            106.62744043912511,
                                            -6.252471168809336
                                        ],
                                        [
                                            106.62738534665658,
                                            -6.252562463486811
                                        ],
                                        [
                                            106.62732671175854,
                                            -6.252651520651057
                                        ],
                                        [
                                            106.62726462256433,
                                            -6.252738202705814
                                        ],
                                        [
                                            106.62719917799973,
                                            -6.252822375652045
                                        ],
                                        [
                                            106.62616043225819,
                                            -6.254105503166329
                                        ],
                                        [
                                            106.62613065390667,
                                            -6.25414164512074
                                        ],
                                        [
                                            106.62604185125059,
                                            -6.254242374585885
                                        ],
                                        [
                                            106.6259481742689,
                                            -6.2543385813604
                                        ],
                                        [
                                            106.62453054774676,
                                            -6.255724142555096
                                        ],
                                        [
                                            106.62327724085202,
                                            -6.257315288769519
                                        ],
                                        [
                                            106.6226758830856,
                                            -6.258488723275889
                                        ],
                                        [
                                            106.62151321706136,
                                            -6.26165759422247
                                        ],
                                        [
                                            106.6205246687785,
                                            -6.264715546385276
                                        ],
                                        [
                                            106.61998034871425,
                                            -6.266500462326348
                                        ],
                                        [
                                            106.61738735679796,
                                            -6.265708685314848
                                        ],
                                        [
                                            106.61479437216258,
                                            -6.264916895598219
                                        ],
                                        [
                                            106.6153453112372,
                                            -6.26311033297543
                                        ],
                                        [
                                            106.61535887211426,
                                            -6.263067160121238
                                        ],
                                        [
                                            106.61637067596598,
                                            -6.259937362019571
                                        ],
                                        [
                                            106.61640256862376,
                                            -6.259844484535222
                                        ],
                                        [
                                            106.61640518025501,
                                            -6.259837337622912
                                        ],
                                        [
                                            106.61764316450063,
                                            -6.256463271063069
                                        ],
                                        [
                                            106.61767283853078,
                                            -6.256386057970076
                                        ],
                                        [
                                            106.6177048498991,
                                            -6.256309785568078
                                        ],
                                        [
                                            106.61773917162554,
                                            -6.256234524903277
                                        ],
                                        [
                                            106.61777577043557,
                                            -6.256160347022274
                                        ],
                                        [
                                            106.6185728404642,
                                            -6.254605046885331
                                        ],
                                        [
                                            106.6186373407408,
                                            -6.254486543219343
                                        ],
                                        [
                                            106.61868761644052,
                                            -6.254402916161609
                                        ],
                                        [
                                            106.61874086619815,
                                            -6.254321153398394
                                        ],
                                        [
                                            106.61879701986675,
                                            -6.254241359251296
                                        ],
                                        [
                                            106.61885600639971,
                                            -6.254163638940724
                                        ],
                                        [
                                            106.62038128446875,
                                            -6.252227227704338
                                        ],
                                        [
                                            106.62043367087733,
                                            -6.252162775091904
                                        ],
                                        [
                                            106.62052247713075,
                                            -6.252062043828232
                                        ],
                                        [
                                            106.6206161577096,
                                            -6.251965835255021
                                        ],
                                        [
                                            106.62204678842852,
                                            -6.25056757293504
                                        ],
                                        [
                                            106.62275362228183,
                                            -6.249694453536165
                                        ],
                                        [
                                            106.62291196861258,
                                            -6.249329848593561
                                        ],
                                        [
                                            106.62306614568615,
                                            -6.248923167969792
                                        ],
                                        [
                                            106.62334150100958,
                                            -6.247459372951539
                                        ],
                                        [
                                            106.6233562786694,
                                            -6.247386344404219
                                        ],
                                        [
                                            106.62337305552222,
                                            -6.247313750229296
                                        ],
                                        [
                                            106.62355046478228,
                                            -6.246591410265353
                                        ],
                                        [
                                            106.62356890538086,
                                            -6.246520476238913
                                        ],
                                        [
                                            106.62358925434069,
                                            -6.246450066517298
                                        ],
                                        [
                                            106.6236114963736,
                                            -6.246380233261107
                                        ],
                                        [
                                            106.62367848417489,
                                            -6.246200715990199
                                        ],
                                        [
                                            106.62372612036427,
                                            -6.246092381857864
                                        ],
                                        [
                                            106.62377843392773,
                                            -6.245986229480877
                                        ],
                                        [
                                            106.62383532414094,
                                            -6.245882462105897
                                        ],
                                        [
                                            106.62387966611374,
                                            -6.245808357069905
                                        ],
                                        [
                                            106.6239263436259,
                                            -6.245735702640502
                                        ],
                                        [
                                            106.62459516133765,
                                            -6.244730223720751
                                        ],
                                        [
                                            106.62466881671264,
                                            -6.244624983256301
                                        ],
                                        [
                                            106.62527116283405,
                                            -6.243806305216651
                                        ],
                                        [
                                            106.62623449682457,
                                            -6.242467523157643
                                        ],
                                        [
                                            106.62644295248037,
                                            -6.24214280854369
                                        ],
                                        [
                                            106.6266351187158,
                                            -6.2413971257767
                                        ],
                                        [
                                            106.62666586653665,
                                            -6.241026271445207
                                        ],
                                        [
                                            106.62667898944386,
                                            -6.240902514839149
                                        ],
                                        [
                                            106.62669777088547,
                                            -6.240779490281227
                                        ],
                                        [
                                            106.62672084658988,
                                            -6.240663405791508
                                        ],
                                        [
                                            106.62674895939705,
                                            -6.240548440058376
                                        ],
                                        [
                                            106.62678205714627,
                                            -6.240434810717886
                                        ],
                                        [
                                            106.62682007598573,
                                            -6.240322733607229
                                        ],
                                        [
                                            106.62686294396974,
                                            -6.240212422765012
                                        ],
                                        [
                                            106.62691058015935,
                                            -6.240104088632677
                                        ],
                                        [
                                            106.62696289282337,
                                            -6.239997936255577
                                        ],
                                        [
                                            106.62701978303664,
                                            -6.239894168880767
                                        ],
                                        [
                                            106.6270274236768,
                                            -6.239881010000488
                                        ],
                                        [
                                            106.62714618454885,
                                            -6.239677810882142
                                        ],
                                        [
                                            106.62734985401272,
                                            -6.239265019365121
                                        ],
                                        [
                                            106.62739012115736,
                                            -6.239186640750745
                                        ],
                                        [
                                            106.6274329109001,
                                            -6.239109612918185
                                        ],
                                        [
                                            106.62749426984487,
                                            -6.239008427496913
                                        ],
                                        [
                                            106.62755998060868,
                                            -6.238910016483885
                                        ],
                                        [
                                            106.6276299190855,
                                            -6.238814566938629
                                        ],
                                        [
                                            106.62770395037705,
                                            -6.23872226142305
                                        ],
                                        [
                                            106.62779188698613,
                                            -6.238622466353661
                                        ],
                                        [
                                            106.62780754867958,
                                            -6.238606359495861
                                        ],
                                        [
                                            106.62808913810335,
                                            -6.237898620924568
                                        ],
                                        [
                                            106.62936201694356,
                                            -6.234294692146307
                                        ],
                                        [
                                            106.62937056140237,
                                            -6.234270854715987
                                        ],
                                        [
                                            106.62938531747858,
                                            -6.234231248573167
                                        ],
                                        [
                                            106.63069148472442,
                                            -6.2308070430106
                                        ],
                                        [
                                            106.63181098868631,
                                            -6.227591295801631
                                        ],
                                        [
                                            106.6318235755977,
                                            -6.227555928163497
                                        ],
                                        [
                                            106.63184122928936,
                                            -6.227508759621514
                                        ],
                                        [
                                            106.63227389042777,
                                            -6.226384583681465
                                        ]
                                    ]
                                ]
                            ],
                            "type": "MultiPolygon"
                        },
                        "id": "53",
                        "properties": {
                            "ALAMAT": "Jl. Gading Serpong",
                            "DESA": "CURUG SANGERENG",
                            "KABKOT": "TANGERANG",
                            "KECAMATAN": "KELAPA DUA",
                            "NAMA": "CBD Gading Serpong",
                            "PROVINSI": "BANTEN"
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            },
            "provinsi": "BANTEN"
        },
        "point": {
            "10": {
                "features": [],
                "type": "FeatureCollection"
            },
            "15": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                106.65799470000002,
                                -6.29840045999996
                            ],
                            "type": "Point"
                        },
                        "id": "0",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6611.84418378,
                            "gid": 2154126,
                            "id_brand": 963,
                            "id_merchant": 1277068.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29840046,
                            "longitude": 106.6579947,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62820738-LENGKONG GUDANG",
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
                                106.66329130000003,
                                -6.298010939999972
                            ],
                            "type": "Point"
                        },
                        "id": "1",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6881.27460335,
                            "gid": 2154302,
                            "id_brand": 963,
                            "id_merchant": 1277245.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29801094,
                            "longitude": 106.6632913,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62736614-LENGKONG GUDANG",
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
                                106.66111130000004,
                                -6.276299950000026
                            ],
                            "type": "Point"
                        },
                        "id": "2",
                        "properties": {
                            "alamat_merchant": "PAHLAWAN SERIBU",
                            "developer_name": null,
                            "dist": 4875.40561648,
                            "gid": 2164351,
                            "id_brand": 963,
                            "id_merchant": 1287308.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27629995,
                            "longitude": 106.6611113,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "CNI",
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
                                106.65894749999998,
                                -6.2748886899999645
                            ],
                            "type": "Point"
                        },
                        "id": "3",
                        "properties": {
                            "alamat_merchant": "PAHLAWAN SERIBU",
                            "developer_name": null,
                            "dist": 4593.47880423,
                            "gid": 2164941,
                            "id_brand": 963,
                            "id_merchant": 1287899.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27488869,
                            "longitude": 106.6589475,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "ALFAMART",
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
                                106.65843730000005,
                                -6.27457901000001
                            ],
                            "type": "Point"
                        },
                        "id": "4",
                        "properties": {
                            "alamat_merchant": "PAHLAWAN SERIBU",
                            "developer_name": null,
                            "dist": 4528.84438594,
                            "gid": 2165065,
                            "id_brand": 963,
                            "id_merchant": 1288024.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27457901,
                            "longitude": 106.6584373,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "CLINDERMA",
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
                                106.65741200000004,
                                -6.273739560000009
                            ],
                            "type": "Point"
                        },
                        "id": "5",
                        "properties": {
                            "alamat_merchant": "RAYA SERPONG",
                            "developer_name": null,
                            "dist": 4382.39640203,
                            "gid": 2165502,
                            "id_brand": 963,
                            "id_merchant": 1288461.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27373956,
                            "longitude": 106.657412,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62393106-LENGKONG KARYA",
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
                                106.65716820000003,
                                -6.273343820000039
                            ],
                            "type": "Point"
                        },
                        "id": "6",
                        "properties": {
                            "alamat_merchant": "RAYA SERPONG",
                            "developer_name": null,
                            "dist": 4332.55311099,
                            "gid": 2165662,
                            "id_brand": 963,
                            "id_merchant": 1288621.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27334382,
                            "longitude": 106.6571682,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "TOKO DUNIA CANTIK",
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
                                106.65637549999998,
                                -6.2720024299999855
                            ],
                            "type": "Point"
                        },
                        "id": "7",
                        "properties": {
                            "alamat_merchant": "RAYA SERPONG",
                            "developer_name": null,
                            "dist": 4166.65526902,
                            "gid": 2166254,
                            "id_brand": 963,
                            "id_merchant": 1289216.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27200243,
                            "longitude": 106.6563755,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "INDOMARET",
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
                                106.65593129999999,
                                -6.271381049999998
                            ],
                            "type": "Point"
                        },
                        "id": "8",
                        "properties": {
                            "alamat_merchant": "RAYA SERPONG",
                            "developer_name": null,
                            "dist": 4083.72947123,
                            "gid": 2166514,
                            "id_brand": 963,
                            "id_merchant": 1289476.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.27138105,
                            "longitude": 106.6559313,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "ALFAMART",
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
                                106.6553023,
                                -6.269832310000019
                            ],
                            "type": "Point"
                        },
                        "id": "9",
                        "properties": {
                            "alamat_merchant": "RAYA SERPONG",
                            "developer_name": null,
                            "dist": 3916.89510949,
                            "gid": 2167265,
                            "id_brand": 963,
                            "id_merchant": 1290226.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.26983231,
                            "longitude": 106.6553023,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "GIANT EKSTRA",
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
                                106.65558680000001,
                                -6.269660600000022
                            ],
                            "type": "Point"
                        },
                        "id": "10",
                        "properties": {
                            "alamat_merchant": "SERPONG RAYA",
                            "developer_name": null,
                            "dist": 3928.03497324,
                            "gid": 2167351,
                            "id_brand": 963,
                            "id_merchant": 1290314.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.2696606,
                            "longitude": 106.6555868,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "BEAUTY CORNER",
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
                                106.65519420000003,
                                -6.2696509800000255
                            ],
                            "type": "Point"
                        },
                        "id": "11",
                        "properties": {
                            "alamat_merchant": "SERPONG RAYA",
                            "developer_name": null,
                            "dist": 3894.60972658,
                            "gid": 2167354,
                            "id_brand": 963,
                            "id_merchant": 1290317.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.26965098,
                            "longitude": 106.6551942,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "GUARDIAN",
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
