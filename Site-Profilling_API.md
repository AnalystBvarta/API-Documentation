# API Site Profilling

#### Postman
<a href="site-profilling.postman_collection.json" download>Download Postman Collection</a>

## HTTP Request Login
```URL
POST http://ALBApiAuthV2-606248699.ap-southeast-1.elb.amazonaws.com/users/login
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
curl --location --request POST 'http://ALBApiAuthV2-606248699.ap-southeast-1.elb.amazonaws.com/users/login' \
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
POST http://ALBSiteClient-1530194231.ap-southeast-1.elb.amazonaws.com/api/v1.0/drivetime
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
|batas_informal||berisi geojson batas informal|
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
curl --location --request POST 'http://ALBSiteClient-1530194231.ap-southeast-1.elb.amazonaws.com/api/v1.0/drivetime' \
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
    "Gading Serpong": {
        "area": {
            "10": {
                "features": [
                    {
                        "geometry": {
                            "coordinates": [
                                [
                                    [
                                        106.603792,
                                        -6.260451
                                    ],
                                    [
                                        106.604879,
                                        -6.252854
                                    ],
                                    [
                                        106.605422,
                                        -6.247857
                                    ],
                                    [
                                        106.6055,
                                        -6.247461
                                    ],
                                    [
                                        106.606484,
                                        -6.242779
                                    ],
                                    [
                                        106.609044,
                                        -6.233232
                                    ],
                                    [
                                        106.611787,
                                        -6.22585
                                    ],
                                    [
                                        106.61447,
                                        -6.223666
                                    ],
                                    [
                                        106.618055,
                                        -6.22399
                                    ],
                                    [
                                        106.629509,
                                        -6.224404
                                    ],
                                    [
                                        106.630046,
                                        -6.219998
                                    ],
                                    [
                                        106.629751,
                                        -6.218825
                                    ],
                                    [
                                        106.628697,
                                        -6.216707
                                    ],
                                    [
                                        106.629273,
                                        -6.214442
                                    ],
                                    [
                                        106.6294,
                                        -6.214364
                                    ],
                                    [
                                        106.631517,
                                        -6.214469
                                    ],
                                    [
                                        106.635275,
                                        -6.218309
                                    ],
                                    [
                                        106.641493,
                                        -6.227336
                                    ],
                                    [
                                        106.640543,
                                        -6.23049
                                    ],
                                    [
                                        106.642191,
                                        -6.241536
                                    ],
                                    [
                                        106.643294,
                                        -6.242192
                                    ],
                                    [
                                        106.644837,
                                        -6.244053
                                    ],
                                    [
                                        106.646001,
                                        -6.249967
                                    ],
                                    [
                                        106.647198,
                                        -6.260286
                                    ],
                                    [
                                        106.647225,
                                        -6.260546
                                    ],
                                    [
                                        106.646093,
                                        -6.270127
                                    ],
                                    [
                                        106.645602,
                                        -6.274481
                                    ],
                                    [
                                        106.645581,
                                        -6.274525
                                    ],
                                    [
                                        106.635616,
                                        -6.278154
                                    ],
                                    [
                                        106.633715,
                                        -6.278237
                                    ],
                                    [
                                        106.63356,
                                        -6.277951
                                    ],
                                    [
                                        106.632525,
                                        -6.275587
                                    ],
                                    [
                                        106.630432,
                                        -6.27289
                                    ],
                                    [
                                        106.620957,
                                        -6.269979
                                    ],
                                    [
                                        106.617831,
                                        -6.272543
                                    ],
                                    [
                                        106.614329,
                                        -6.271709
                                    ],
                                    [
                                        106.614598,
                                        -6.27058
                                    ],
                                    [
                                        106.606919,
                                        -6.262236
                                    ],
                                    [
                                        106.605092,
                                        -6.263088
                                    ],
                                    [
                                        106.604878,
                                        -6.263026
                                    ],
                                    [
                                        106.604797,
                                        -6.262868
                                    ],
                                    [
                                        106.603792,
                                        -6.260451
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "28,047",
                            "age": {
                                "0": {
                                    "persen": 15.265430274199279,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 13134.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 16.917034996266977,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 14555.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 16.758964452846005,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 14419.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 17.549317169950886,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 15099.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 17.48887843276051,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 15047.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 18.033989350881377,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 15516.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 18.903377339696746,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 16264.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 18.00376998228619,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 15490.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 14.430910787609125,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 12416.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 17.26223316829661,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 14852.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 9.329648912060119,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 8027.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 5.860232940651192,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 5042.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 4.358562778151918,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 3750.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 2.0142371452099397,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 1733.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 86038,
                                    "persen": 49.20267788651526,
                                    "total": 42333
                                },
                                "male": {
                                    "from": 86038,
                                    "persen": 50.796159836351386,
                                    "total": 43704
                                },
                                "total": {
                                    "from": 738441,
                                    "persen": 11.651303218537432,
                                    "total": 86038
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 10.0,
                            "high": 0,
                            "kabupaten": "TANGERANG",
                            "kecamatan": "KELAPA DUA",
                            "ket": "Gading Serpong",
                            "kodepodes": "3603051002",
                            "latitude": -692363.677,
                            "longitude": 11869631.657,
                            "low": 0,
                            "luas_m": 22934293760.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "CURUG SANGERENG",
                            "provinsi": "BANTEN",
                            "ses": {
                                "high": 71.517,
                                "low": 0,
                                "medium_high": 23.511,
                                "medium_low": 4.971
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
                                        106.555559,
                                        -6.218546
                                    ],
                                    [
                                        106.557229,
                                        -6.215356
                                    ],
                                    [
                                        106.56481,
                                        -6.216431
                                    ],
                                    [
                                        106.564919,
                                        -6.216457
                                    ],
                                    [
                                        106.575179,
                                        -6.219864
                                    ],
                                    [
                                        106.586741,
                                        -6.222456
                                    ],
                                    [
                                        106.59295,
                                        -6.218019
                                    ],
                                    [
                                        106.59477,
                                        -6.214534
                                    ],
                                    [
                                        106.598088,
                                        -6.205778
                                    ],
                                    [
                                        106.598121,
                                        -6.20539
                                    ],
                                    [
                                        106.598177,
                                        -6.204016
                                    ],
                                    [
                                        106.598197,
                                        -6.203687
                                    ],
                                    [
                                        106.598412,
                                        -6.201954
                                    ],
                                    [
                                        106.599467,
                                        -6.200032
                                    ],
                                    [
                                        106.599584,
                                        -6.199887
                                    ],
                                    [
                                        106.601923,
                                        -6.199697
                                    ],
                                    [
                                        106.60879,
                                        -6.190969
                                    ],
                                    [
                                        106.608797,
                                        -6.190752
                                    ],
                                    [
                                        106.60777,
                                        -6.186006
                                    ],
                                    [
                                        106.607766,
                                        -6.185882
                                    ],
                                    [
                                        106.609228,
                                        -6.184053
                                    ],
                                    [
                                        106.609419,
                                        -6.184037
                                    ],
                                    [
                                        106.612319,
                                        -6.18366
                                    ],
                                    [
                                        106.620274,
                                        -6.178704
                                    ],
                                    [
                                        106.620498,
                                        -6.178424
                                    ],
                                    [
                                        106.625253,
                                        -6.172927
                                    ],
                                    [
                                        106.625508,
                                        -6.172871
                                    ],
                                    [
                                        106.634804,
                                        -6.173683
                                    ],
                                    [
                                        106.642306,
                                        -6.177915
                                    ],
                                    [
                                        106.645843,
                                        -6.178584
                                    ],
                                    [
                                        106.649749,
                                        -6.183226
                                    ],
                                    [
                                        106.650838,
                                        -6.184859
                                    ],
                                    [
                                        106.650842,
                                        -6.184906
                                    ],
                                    [
                                        106.650835,
                                        -6.185195
                                    ],
                                    [
                                        106.650807,
                                        -6.185321
                                    ],
                                    [
                                        106.64913,
                                        -6.186773
                                    ],
                                    [
                                        106.646174,
                                        -6.198016
                                    ],
                                    [
                                        106.648788,
                                        -6.209675
                                    ],
                                    [
                                        106.650106,
                                        -6.21129
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
                                        106.70004,
                                        -6.204266
                                    ],
                                    [
                                        106.701147,
                                        -6.203384
                                    ],
                                    [
                                        106.702033,
                                        -6.20284
                                    ],
                                    [
                                        106.704263,
                                        -6.205666
                                    ],
                                    [
                                        106.702059,
                                        -6.207405
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
                                        106.671199,
                                        -6.241326
                                    ],
                                    [
                                        106.670846,
                                        -6.242001
                                    ],
                                    [
                                        106.669665,
                                        -6.243947
                                    ],
                                    [
                                        106.660513,
                                        -6.251135
                                    ],
                                    [
                                        106.659946,
                                        -6.257736
                                    ],
                                    [
                                        106.658525,
                                        -6.265175
                                    ],
                                    [
                                        106.658523,
                                        -6.26523
                                    ],
                                    [
                                        106.659392,
                                        -6.273812
                                    ],
                                    [
                                        106.664056,
                                        -6.277214
                                    ],
                                    [
                                        106.664092,
                                        -6.277238
                                    ],
                                    [
                                        106.667806,
                                        -6.281852
                                    ],
                                    [
                                        106.668144,
                                        -6.285436
                                    ],
                                    [
                                        106.667538,
                                        -6.286188
                                    ],
                                    [
                                        106.666586,
                                        -6.297645
                                    ],
                                    [
                                        106.668123,
                                        -6.299339
                                    ],
                                    [
                                        106.668122,
                                        -6.299401
                                    ],
                                    [
                                        106.66672,
                                        -6.301242
                                    ],
                                    [
                                        106.664798,
                                        -6.302585
                                    ],
                                    [
                                        106.655707,
                                        -6.310409
                                    ],
                                    [
                                        106.653708,
                                        -6.313577
                                    ],
                                    [
                                        106.65002,
                                        -6.319165
                                    ],
                                    [
                                        106.640778,
                                        -6.324319
                                    ],
                                    [
                                        106.640591,
                                        -6.324316
                                    ],
                                    [
                                        106.639532,
                                        -6.322876
                                    ],
                                    [
                                        106.639043,
                                        -6.322064
                                    ],
                                    [
                                        106.639044,
                                        -6.322064
                                    ],
                                    [
                                        106.638931,
                                        -6.311701
                                    ],
                                    [
                                        106.633508,
                                        -6.309334
                                    ],
                                    [
                                        106.629576,
                                        -6.310242
                                    ],
                                    [
                                        106.628087,
                                        -6.309936
                                    ],
                                    [
                                        106.622964,
                                        -6.301099
                                    ],
                                    [
                                        106.619474,
                                        -6.300215
                                    ],
                                    [
                                        106.619405,
                                        -6.297255
                                    ],
                                    [
                                        106.617338,
                                        -6.29214
                                    ],
                                    [
                                        106.616977,
                                        -6.289171
                                    ],
                                    [
                                        106.615202,
                                        -6.283329
                                    ],
                                    [
                                        106.60464,
                                        -6.287401
                                    ],
                                    [
                                        106.604497,
                                        -6.287894
                                    ],
                                    [
                                        106.59669,
                                        -6.296168
                                    ],
                                    [
                                        106.596495,
                                        -6.296623
                                    ],
                                    [
                                        106.596228,
                                        -6.297087
                                    ],
                                    [
                                        106.594654,
                                        -6.303103
                                    ],
                                    [
                                        106.593695,
                                        -6.304606
                                    ],
                                    [
                                        106.591119,
                                        -6.307098
                                    ],
                                    [
                                        106.584009,
                                        -6.3036
                                    ],
                                    [
                                        106.582774,
                                        -6.300281
                                    ],
                                    [
                                        106.582738,
                                        -6.3001
                                    ],
                                    [
                                        106.582208,
                                        -6.295302
                                    ],
                                    [
                                        106.582211,
                                        -6.295293
                                    ],
                                    [
                                        106.587752,
                                        -6.287653
                                    ],
                                    [
                                        106.587687,
                                        -6.284301
                                    ],
                                    [
                                        106.587691,
                                        -6.283627
                                    ],
                                    [
                                        106.587761,
                                        -6.28088
                                    ],
                                    [
                                        106.588099,
                                        -6.278644
                                    ],
                                    [
                                        106.588561,
                                        -6.270439
                                    ],
                                    [
                                        106.585772,
                                        -6.266667
                                    ],
                                    [
                                        106.582965,
                                        -6.264996
                                    ],
                                    [
                                        106.581327,
                                        -6.263584
                                    ],
                                    [
                                        106.574229,
                                        -6.259537
                                    ],
                                    [
                                        106.573515,
                                        -6.25827
                                    ],
                                    [
                                        106.573532,
                                        -6.257892
                                    ],
                                    [
                                        106.574961,
                                        -6.256012
                                    ],
                                    [
                                        106.575169,
                                        -6.256055
                                    ],
                                    [
                                        106.576797,
                                        -6.256289
                                    ],
                                    [
                                        106.582765,
                                        -6.256515
                                    ],
                                    [
                                        106.583007,
                                        -6.25655
                                    ],
                                    [
                                        106.5885,
                                        -6.256264
                                    ],
                                    [
                                        106.593299,
                                        -6.251746
                                    ],
                                    [
                                        106.595036,
                                        -6.249953
                                    ],
                                    [
                                        106.59308,
                                        -6.238876
                                    ],
                                    [
                                        106.586011,
                                        -6.238914
                                    ],
                                    [
                                        106.58368,
                                        -6.240748
                                    ],
                                    [
                                        106.582385,
                                        -6.240703
                                    ],
                                    [
                                        106.582194,
                                        -6.240625
                                    ],
                                    [
                                        106.580649,
                                        -6.238806
                                    ],
                                    [
                                        106.580898,
                                        -6.238417
                                    ],
                                    [
                                        106.583441,
                                        -6.234442
                                    ],
                                    [
                                        106.584859,
                                        -6.229136
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
                                        106.557013,
                                        -6.219307
                                    ],
                                    [
                                        106.555559,
                                        -6.218546
                                    ]
                                ],
                                [
                                    [
                                        106.603792,
                                        -6.260451
                                    ],
                                    [
                                        106.604797,
                                        -6.262868
                                    ],
                                    [
                                        106.604878,
                                        -6.263026
                                    ],
                                    [
                                        106.605092,
                                        -6.263088
                                    ],
                                    [
                                        106.606919,
                                        -6.262236
                                    ],
                                    [
                                        106.614598,
                                        -6.27058
                                    ],
                                    [
                                        106.614329,
                                        -6.271709
                                    ],
                                    [
                                        106.617831,
                                        -6.272543
                                    ],
                                    [
                                        106.620957,
                                        -6.269979
                                    ],
                                    [
                                        106.630432,
                                        -6.27289
                                    ],
                                    [
                                        106.632525,
                                        -6.275587
                                    ],
                                    [
                                        106.63356,
                                        -6.277951
                                    ],
                                    [
                                        106.633715,
                                        -6.278237
                                    ],
                                    [
                                        106.635616,
                                        -6.278154
                                    ],
                                    [
                                        106.645581,
                                        -6.274525
                                    ],
                                    [
                                        106.645602,
                                        -6.274481
                                    ],
                                    [
                                        106.646093,
                                        -6.270127
                                    ],
                                    [
                                        106.647225,
                                        -6.260546
                                    ],
                                    [
                                        106.647198,
                                        -6.260286
                                    ],
                                    [
                                        106.646001,
                                        -6.249967
                                    ],
                                    [
                                        106.644837,
                                        -6.244053
                                    ],
                                    [
                                        106.643294,
                                        -6.242192
                                    ],
                                    [
                                        106.642191,
                                        -6.241536
                                    ],
                                    [
                                        106.640543,
                                        -6.23049
                                    ],
                                    [
                                        106.641493,
                                        -6.227336
                                    ],
                                    [
                                        106.635275,
                                        -6.218309
                                    ],
                                    [
                                        106.631517,
                                        -6.214469
                                    ],
                                    [
                                        106.6294,
                                        -6.214364
                                    ],
                                    [
                                        106.629273,
                                        -6.214442
                                    ],
                                    [
                                        106.628697,
                                        -6.216707
                                    ],
                                    [
                                        106.629751,
                                        -6.218825
                                    ],
                                    [
                                        106.630046,
                                        -6.219998
                                    ],
                                    [
                                        106.629509,
                                        -6.224404
                                    ],
                                    [
                                        106.618055,
                                        -6.22399
                                    ],
                                    [
                                        106.61447,
                                        -6.223666
                                    ],
                                    [
                                        106.611787,
                                        -6.22585
                                    ],
                                    [
                                        106.609044,
                                        -6.233232
                                    ],
                                    [
                                        106.606484,
                                        -6.242779
                                    ],
                                    [
                                        106.6055,
                                        -6.247461
                                    ],
                                    [
                                        106.605422,
                                        -6.247857
                                    ],
                                    [
                                        106.604879,
                                        -6.252854
                                    ],
                                    [
                                        106.603792,
                                        -6.260451
                                    ]
                                ]
                            ],
                            "type": "Polygon"
                        },
                        "id": "0",
                        "properties": {
                            "Household": "243,551",
                            "age": {
                                "0": {
                                    "persen": 15.329185588744885,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 113197.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "10": {
                                    "persen": 15.82915778936545,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 116889.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "15": {
                                    "persen": 15.940067115559447,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 117708.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "20": {
                                    "persen": 17.322574210937386,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 127917.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "25": {
                                    "persen": 17.955529266652587,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 132591.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "30": {
                                    "persen": 18.584150868841284,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 137233.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "35": {
                                    "persen": 18.510346738467987,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 136688.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "40": {
                                    "persen": 16.554740414209704,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 122247.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "45": {
                                    "persen": 13.5872726915124,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 100334.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "5": {
                                    "persen": 16.292295635010717,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 120309.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "50": {
                                    "persen": 10.024632211034115,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 74026.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "55": {
                                    "persen": 7.121760029966284,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 52590.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "60": {
                                    "persen": 5.567268997755161,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 41111.0,
                                    "total_female": null,
                                    "total_male": null
                                },
                                "65": {
                                    "persen": 2.6030513652027363,
                                    "persen_female": null,
                                    "persen_male": null,
                                    "total": 19222.0,
                                    "total_female": null,
                                    "total_male": null
                                }
                            },
                            "demography": {
                                "female": {
                                    "from": 738441,
                                    "persen": 49.486282587234456,
                                    "total": 365427
                                },
                                "male": {
                                    "from": 738441,
                                    "persen": 50.513717412765544,
                                    "total": 373014
                                },
                                "total": {
                                    "from": 738441,
                                    "persen": 100.0,
                                    "total": 738441
                                }
                            },
                            "driving_unit": "time",
                            "durasi_distance": 15.0,
                            "high": 0,
                            "kabupaten": "TANGERANG",
                            "kecamatan": "KELAPA DUA",
                            "ket": "Gading Serpong",
                            "kodepodes": "3603051002",
                            "latitude": -692127.938,
                            "longitude": 11869774.187,
                            "low": 0,
                            "luas_m": 112312742480.0,
                            "medium_high": 0,
                            "medium_low": 0,
                            "nama_desa": "CURUG SANGERENG",
                            "poi": {
                                "Office Building": {
                                    "kode_sub_kategori": "2603",
                                    "min_dist": 2113.17143696,
                                    "tot": 4
                                },
                                "Store": {
                                    "kode_sub_kategori": "1610",
                                    "min_dist": 2113.17143696,
                                    "tot": 110
                                }
                            },
                            "provinsi": "BANTEN",
                            "ses": {
                                "high": 35.461999999999996,
                                "low": 4.760999999999999,
                                "medium_high": 23.215000000000003,
                                "medium_low": 36.561
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
        "batas_informal": {
            "features": [
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
                        "NAMA": "CBD Gading Serpong",
                        "fid": 54
                    },
                    "type": "Feature"
                }
            ],
            "type": "FeatureCollection"
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
                                106.6621541,
                                -6.298261840000037
                            ],
                            "type": "Point"
                        },
                        "id": "0",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6877.85379632,
                            "gid": 2154196,
                            "id_brand": 963,
                            "id_merchant": 1277137.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29826184,
                            "longitude": 106.6621541,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62739953-LENGKONG GUDANG",
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
                                106.66245290000003,
                                -6.297878370000016
                            ],
                            "type": "Point"
                        },
                        "id": "1",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6860.52120857,
                            "gid": 2154363,
                            "id_brand": 963,
                            "id_merchant": 1277304.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29787837,
                            "longitude": 106.6624529,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62739279-LENGKONG GUDANG",
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
                                106.66243690000005,
                                -6.297326610000016
                            ],
                            "type": "Point"
                        },
                        "id": "2",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6808.58053285,
                            "gid": 2154558,
                            "id_brand": 963,
                            "id_merchant": 1277501.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29732661,
                            "longitude": 106.6624369,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62733315-LENGKONG GUDANG",
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
                                106.66123479999996,
                                -6.297215990000011
                            ],
                            "type": "Point"
                        },
                        "id": "3",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6724.91084658,
                            "gid": 2154613,
                            "id_brand": 963,
                            "id_merchant": 1277556.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29721599,
                            "longitude": 106.6612348,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62769445-LENGKONG GUDANG",
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
                                106.66093459999999,
                                -6.297138580000001
                            ],
                            "type": "Point"
                        },
                        "id": "4",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6699.61916971,
                            "gid": 2154637,
                            "id_brand": 963,
                            "id_merchant": 1277580.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29713858,
                            "longitude": 106.6609346,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62773134-LENGKONG GUDANG",
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
                                106.65829359999996,
                                -6.29679650000003
                            ],
                            "type": "Point"
                        },
                        "id": "5",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6512.97646996,
                            "gid": 2154808,
                            "id_brand": 963,
                            "id_merchant": 1277750.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.2967965,
                            "longitude": 106.6582936,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62784558-LENGKONG GUDANG",
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
                                106.6606415,
                                -6.296768009999982
                            ],
                            "type": "Point"
                        },
                        "id": "6",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6647.42745749,
                            "gid": 2154821,
                            "id_brand": 963,
                            "id_merchant": 1277763.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29676801,
                            "longitude": 106.6606415,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62773154-LENGKONG GUDANG",
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
                                106.66312170000003,
                                -6.296767520000031
                            ],
                            "type": "Point"
                        },
                        "id": "7",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6800.03600002,
                            "gid": 2154822,
                            "id_brand": 963,
                            "id_merchant": 1277764.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29676752,
                            "longitude": 106.6631217,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62733064-LENGKONG GUDANG",
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
                                106.66304159999999,
                                -6.29673960000003
                            ],
                            "type": "Point"
                        },
                        "id": "8",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6792.43586964,
                            "gid": 2154833,
                            "id_brand": 963,
                            "id_merchant": 1277775.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.2967396,
                            "longitude": 106.6630416,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62733104-LENGKONG GUDANG",
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
                                106.66255629999998,
                                -6.296732759999997
                            ],
                            "type": "Point"
                        },
                        "id": "9",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6761.37171309,
                            "gid": 2154836,
                            "id_brand": 963,
                            "id_merchant": 1277778.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29673276,
                            "longitude": 106.6625563,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62733250-LENGKONG GUDANG",
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
                                106.6615004,
                                -6.296440539999977
                            ],
                            "type": "Point"
                        },
                        "id": "10",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6669.09814369,
                            "gid": 2154992,
                            "id_brand": 963,
                            "id_merchant": 1277936.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29644054,
                            "longitude": 106.6615004,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62776505-LENGKONG GUDANG",
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
                                106.65983209999999,
                                -6.296095370000017
                            ],
                            "type": "Point"
                        },
                        "id": "11",
                        "properties": {
                            "alamat_merchant": "SMAPAL",
                            "developer_name": null,
                            "dist": 6536.1499649,
                            "gid": 2155129,
                            "id_brand": 963,
                            "id_merchant": 1278074.0,
                            "kode_brand": "1610008",
                            "kode_kategori": "16",
                            "kode_sub_kategori": "1610",
                            "latitude": -6.29609537,
                            "longitude": 106.6598321,
                            "nama_brand": "UNILEVER",
                            "nama_merchant": "62780531-LENGKONG GUDANG",
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
