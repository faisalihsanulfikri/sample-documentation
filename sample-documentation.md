# Service Admission
Admission service 

## Symbol
- ✅ = Resource available with testcase
- ☑️ = Resource available without testcase
- ⭕ = Resource unavailable but testcase available
- ❌ = Resource unavailable and no testcase available
- ✋ = Resource implementations are pending

## Section
- ☑️ [Healthcheck](#healthcheck)
- ☑️ [Admission](#admission)
- ☑️ [Formulir](#formulir)
- ☑️ [Formulir Status](#formulir-status)
- ☑️ [Location](#location) 
- ✋ [Component](#component)

---

## Healthcheck
- [**0. Health check** | ☑️ ](#health-check)

### Health check
- Endpoint: **GET /**
- Status: ☑️ 

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ping success",
  "data": {
    "name": "Service",
    "version": "1.0"
  }
}
```

---

## Admission
- [**1. Admission list** | ☑️ ](#admission-list)
- [**2. Admission detail** | ☑️ ](#admission-detail)
- [**3. Create admission** | ☑️ ](#create-admission)
- [**4. Update admission** | ☑️ ](#update-admission)
- [**5. Admission ownership** | ☑️ ](#admission-ownership)
- [**6. Admission authorization** | ☑️ ](#admission-authorization)
- [**6. Toggle admission status** | ☑️ ](#toggle-admission-status)
- [**7. Statistic admission** | ✋ ](#statistic-admission)
- [**8. Statistic approval admission**  | ✋ ](#statistic-approval-admission)

### Admission list
- Endpoint: **GET /v1/admission**
- Status: ☑️

**Request Query**
```json
{
  "institution_id": "6041a2c143361e350c114353",
  "limit": "3",
  "offset": "0",
  "show_approval": true,
  "sort_by": "created_at",
  "sort_type": "desc",
  "show_original_max_formulir": false,
  "show_original_total_remaining_formulir": false,
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ping success",
  "data": [
    {
      "id": "6041a2c143361e350c114353",
      "uuid": "123e4567-e89b-12d3-a456-426614174000",
      "name": "PPDB Jalur Zonasi",    
      "thumbnail": null,//null or string, max: 500  
      "status": "active",
      "formated_status": "Tidak Aktif",
      "max_formulirs": 100,
      "total_remaining_formulirs": 55,
      "total_registrants": 45,
      "total_capacities": 200,
      "total_registrants": 55,
      "institution": {
        "id" : "6041a2c143361e350c114353",
        "name" : "EDU OFFICE",
        "logo" : "edulogy.jpg"
      },
      "start_at": "2020-06-09T01:29:00.000Z",
      "finish_at": "2020-06-09T01:29:00.000Z",
      "created_at": "2020-06-09T01:29:00.000Z",
      "updated_at": "2020-06-09T01:29:00.000Z",
    }
  ]
}
```

### Admission detail
- Endpoint: **GET /v1/admission/:identifier**
- Status: ☑️

**Request Query**
```json
{
  "show_original_max_formulir": false,
  "show_original_total_remaining_formulir": false,
}
```

**Success Response**
```json
{
  "id": "5f748a35f3d8b02e44b25f05",
  "uuid": "123e4567-e89b-12d3-a456-426614174000",//uuidv4
  "name": "PPDB Jalur Zonasi",//max: 100
  "description": null,//null or html string, max: 65000
  "thumbnail_id": null,//null or string, max: 500
  "thumbnail": null,//null or object
  "status": "active",//active, inactive
  "max_formulirs": null, //null or integer, min: 1, max: 5000
  "total_remaining_formulirs": 55,
  "total_registrants": 45,
  "total_capacities": null, //null or integer, min: 1, max: 5000
  "total_registrants": 55,
  "show_max_formulir": false,
  "show_remaining_formulir": false,
  "show_approval_at": "2020-06-09 08:29:00",//null or date
  "institution": {
    "id" : "5f748a35f3d8b02e44b25f05",
    "name" : "EDU OFFICE",
    "logo" : "edulogy.jpg"
  },
  "total_schools": 1,
  "schools": [
    {
      "id" : "5f748a35f3d8b02e44b25f05",
      "name" : "EDU SCHOOL",
      "logo" : "edulogy.jpg",
      "longitude" : 103.03940,
      "latitude" : -6.3454
    },
  ],
  "formulir_settings": [
    {
      "field": "citizen_national_identifier", //nik
      "show": false,
      "required": false
    },
    {
      "field": "name",
      "show": true,
      "required": true
    },
    {
      "field": "gender",
      "show": false,
      "required": false
    },
    {
      "field": "birth_place",
      "show": false,
      "required": false
    },
    {
      "field": "birth_at",
      "show": false,
      "required": false,
      "range": { //object or null
        "minimum_total_days": 5000,//null or integer, min: 1
        "maximum_total_days": 6570,//null or integer, min: 1
        "date": "2001-01-01"
      }
    },
    {
      "field": "phone",
      "show": false,
      "required": false
    },
    {
      "field": "email",
      "show": false,
      "required": false
    },
    {
      "field": "photo",
      "show": false,
      "required": false
    },
    {
      "field": "achievement",
      "show": false,
      "required": false
    },
    {
      "field": "address",
      "show": false,
      "required": false,
      "zonation": { //object or null
        "village_ids": [
          "3273201005",
          "3273201005",
        ]
      }
    },
    {
      "field": "school_national_identifier", //nisn
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_name",
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_identifier", //npsn
      "show": false,
      "required": false
    },
    {
      "field": "parent_name",
      "show": false,
      "required": false
    },
    {
      "field": "parent_gender",
      "show": false,
      "required": false
    },
    {
      "field": "parent_phone",
      "show": false,
      "required": false
    },
    {
      "field": "parent_email",
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_family", //kk
      "show": true,
      "required": true
    },
    {
      "field": "document_statement_good", //skck
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_domicile", //tinggal
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_healthy", //sehat
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_unable", //tidak mampu
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_electricity_bill", //rekening listrik
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_graduation",//skl
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_recommendation",//rekomendasi
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_responsibility_parent",//tanggung jawab orangtua wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_assignment_parent",//penugasan orangtua/wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_registered_dtppfm",//Data Terpadu Program Penanganan Fakir Miskin
      "show": false,
      "required": false
    },
    {
      "field": "document_report_school",//rapor
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_school",//ijazah
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kks",//
      "show": false,
      "required": false
    },
    {
      "field": "document_card_pkh",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kip",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kis",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kbpnt",
      "show": false,
      "required": false
    },
    {
      "field": "document_home_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_formal_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_other",
      "show": false,
      "required": false
    },
  ],
  "start_at": "2020-06-09 08:29:00",
  "finish_at": "2020-06-09 08:29:00",
  "created_at": "2020-06-09 08:29:00",
  "updated_at": "2020-06-09 08:29:00",
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

### Create admission
- Endpoint: **POST /v1/admission**
- Status: ☑️

**Request Body**
```json
{
  "name": "PPDB Jalur Zonasi",//max: 100
  "description": null,//null or html string, max: 65000
  "thumbnail": null,//null or string, max: 500
  "status": "active",//active, inactive
  "max_formulirs": 50, // min: 1, max: 5000
  "total_capacities": null, //null or integer, min: 1, max: 5000
  "show_max_formulir": false,
  "show_remaining_formulir": false,
  "show_approval_at": "2020-06-09 08:29:00",//null or date
  "total_schools": 1,
  "institution_id": "5f748a35f3d8b02e44b25f05",
  "school_ids": [
    "5f748a35f3d8b02e44b25f05"
  ],
  "formulir_settings": [
    {
      "field": "citizen_national_identifier", //nik
      "show": false,
      "required": false
    },
    {
      "field": "name",
      "show": true,
      "required": true
    },
    {
      "field": "gender",
      "show": false,
      "required": false
    },
    {
      "field": "birth_place",
      "show": false,
      "required": false
    },
    {
      "field": "birth_at",
      "show": false,
      "required": false,
      "range": { //object or null
        "minimum_total_days": 5000,//null or integer, min: 1
        "maximum_total_days": 6570,//null or integer, min: 1
        "date": "2001-01-01"
      }
    },
    {
      "field": "phone",
      "show": false,
      "required": false
    },
    {
      "field": "email",
      "show": false,
      "required": false
    },
    {
      "field": "photo",
      "show": false,
      "required": false
    },
    {
      "field": "achievement",
      "show": false,
      "required": false
    },
    {
      "field": "address",
      "show": false,
      "required": false,
      "zonation": { //object or null
        "village_ids": [
          "6052fd0b2db1312c687892ef"
        ],
      }
    },
    {
      "field": "school_national_identifier", //nisn
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_name",
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_identifier", //npsn
      "show": false,
      "required": false
    },
    {
      "field": "parent_name",
      "show": false,
      "required": false
    },
    {
      "field": "parent_gender",
      "show": false,
      "required": false
    },
    {
      "field": "parent_phone",
      "show": false,
      "required": false
    },
    {
      "field": "parent_email",
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_birth", //akta
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_family", //kk
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_good", //skck
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_domicile", //tinggal
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_healthy", //sehat
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_unable", //tidak mampu
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_electricity_bill", //rekening listrik
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_graduation",//skl
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_recommendation",//rekomendasi
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_responsibility_parent",//tanggung jawab orangtua wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_assignment_parent",//penugasan orangtua/wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_registered_dtppfm",//Data Terpadu Program Penanganan Fakir Miskin
      "show": false,
      "required": false
    },
    {
      "field": "document_report_school",//rapor
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_school",//ijazah
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kks",//
      "show": false,
      "required": false
    },
    {
      "field": "document_card_pkh",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kip",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kis",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kbpnt",
      "show": false,
      "required": false
    },
    {
      "field": "document_home_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_formal_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_other",
      "show": false,
      "required": false
    },
  ],
  "start_at": "2021-03-07T11:34:51.973Z",
  "finish_at": "2021-03-07T11:34:51.973Z",
}
```

**Success Response**
```json
{
  "id": "5f748a35f3d8b02e44b25f05",
  "uuid": "123e4567-e89b-12d3-a456-426614174000",//uuidv4
  "name": "PPDB Jalur Zonasi",//max: 100
  "description": null,//null or html string, max: 65000
  "thumbnail": null,//null or object
  "max_formulirs": null, //null or integer, min: 1, max: 5000
  "total_remaining_formulirs": 55, //default 0
  "total_capacities": null, //null or integer, min: 1, max: 5000
  "show_max_formulir": false,
  "show_remaining_formulir": false,
  "show_approval_at": "2020-06-09 08:29:00",//null or date
  "total_schools": 1,
  "institution": {
    "id": "5f748a35f3d8b02e44b25f05",
    "name": "Dinas Kota Bandung",
    "logo": "https://image.png"
  },
  "schools": [
    {
      "id": "5f748a35f3d8b02e44b25f05",
      "name": "EDU SCHOOL",
      "logo": "https://image.png"
    }
  ],
  "formulir_settings": [
    {
      "field": "citizen_national_identifier", //nik
      "show": false,
      "required": false
    },
    {
      "field": "name",
      "show": true,
      "required": true
    },
    {
      "field": "gender",
      "show": false,
      "required": false
    },
    {
      "field": "birth_place",
      "show": false,
      "required": false
    },
    {
      "field": "birth_at",
      "show": false,
      "required": false,
      "range": { //object or null
        "minimum_total_days": 5000,//null or integer, min: 1
        "maximum_total_days": 6570,//null or integer, min: 1
        "date": "2001-01-01"
      }
    },
    {
      "field": "phone",
      "show": false,
      "required": false
    },
    {
      "field": "email",
      "show": false,
      "required": false
    },
    {
      "field": "photo",
      "show": false,
      "required": false
    },
    {
      "field": "achievement",
      "show": false,
      "required": false
    },
     {
      "field": "address",
      "show": false,
      "required": false,
      "zonation": { //object or null
        "village_ids": [
          "6052fd0b2db1312c687892ef"
        ],
      }
    },
    {
      "field": "school_national_identifier", //nisn
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_name",
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_identifier", //npsn
      "show": false,
      "required": false
    },
    {
      "field": "parent_name",
      "show": false,
      "required": false
    },
    {
      "field": "parent_gender",
      "show": false,
      "required": false
    },
    {
      "field": "parent_phone",
      "show": false,
      "required": false
    },
    {
      "field": "parent_email",
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_birth", //akta
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_family", //kk
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_good", //skck
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_domicile", //tinggal
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_healthy", //sehat
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_unable", //tidak mampu
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_electricity_bill", //rekening listrik
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_graduation",//skl
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_recommendation",//rekomendasi
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_responsibility_parent",//tanggung jawab orangtua wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_assignment_parent",//penugasan orangtua/wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_registered_dtppfm",//Data Terpadu Program Penanganan Fakir Miskin
      "show": false,
      "required": false
    },
    {
      "field": "document_report_school",//rapor
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_school",//ijazah
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kks",//
      "show": false,
      "required": false
    },
    {
      "field": "document_card_pkh",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kip",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kis",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kbpnt",
      "show": false,
      "required": false
    },
    {
      "field": "document_home_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_formal_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_other",
      "show": false,
      "required": false
    },
  ],
  "start_at": "2020-06-09 08:29:00",
  "finish_at": "2020-06-09 08:29:00",
  "created_at": "2020-06-09 08:29:00",
  "updated_at": "2020-06-09 08:29:00",
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "name",
			"message" : "Name should not greater than 100 character"
		}
	]
}
```

**Error response**
```json
{
	"code": "400",
	"status": "ERROR",
	"message": "Error occured please try again later"
}
```

### Update admission
- Endpoint: **PUT /v1/admission/:identifier**
- Status: ☑️

**Request Body**
```json
{
  "name": "PPDB Jalur Zonasi",//max: 100
  "description": null,//null or html string, max: 65000
  "thumbnail_id": null,//null or string, max: 500
  "status": "active",//active, inactive
  "max_formulirs": null, // min: 1, max: 5000
  "total_capacities": null, //null or integer, min: 1, max: 5000
  "show_max_formulir": false,
  "show_remaining_formulir": false,
  "show_approval_at": "2020-06-09 08:29:00",//null or date
  "total_schools": 1,
  "school_ids": [
    "5f748a35f3d8b02e44b25f05"
  ],
  "formulir_settings": [
    {
      "field": "citizen_national_identifier", //nik
      "show": false,
      "required": false
    },
    {
      "field": "name",
      "show": true,
      "required": true
    },
    {
      "field": "gender",
      "show": false,
      "required": false
    },
    {
      "field": "birth_place",
      "show": false,
      "required": false
    },
    {
      "field": "birth_at",
      "show": false,
      "required": false,
      "range": { //object or null
        "minimum_total_days": 5000,//null or integer, min: 1
        "maximum_total_days": 6570,//null or integer, min: 1
        "date": "2001-01-01"
      }
    },
    {
      "field": "phone",
      "show": false,
      "required": false
    },
    {
      "field": "email",
      "show": false,
      "required": false
    },
    {
      "field": "photo",
      "show": false,
      "required": false
    },
    {
      "field": "achievement",
      "show": false,
      "required": false
    },
    {
      "field": "address",
      "show": false,
      "required": false,
      "zonation": { //object or null
        "village_ids": [
          3273201005, 1571081001,
          1571031007, 3273241001
        ]
      }
    },
    {
      "field": "school_national_identifier", //nisn
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_name",
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_identifier", //npsn
      "show": false,
      "required": false
    },
    {
      "field": "parent_name",
      "show": false,
      "required": false
    },
    {
      "field": "parent_gender",
      "show": false,
      "required": false
    },
    {
      "field": "parent_phone",
      "show": false,
      "required": false
    },
    {
      "field": "parent_email",
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_birth", //akta
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_family", //kk
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_good", //skck
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_domicile", //tinggal
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_healthy", //sehat
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_unable", //tidak mampu
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_electricity_bill", //rekening listrik
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_graduation",//skl
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_recommendation",//rekomendasi
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_responsibility_parent",//tanggung jawab orangtua wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_assignment_parent",//penugasan orangtua/wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_registered_dtppfm",//Data Terpadu Program Penanganan Fakir Miskin
      "show": false,
      "required": false
    },
    {
      "field": "document_report_school",//rapor
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_school",//ijazah
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kks",//
      "show": false,
      "required": false
    },
    {
      "field": "document_card_pkh",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kip",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kis",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kbpnt",
      "show": false,
      "required": false
    },
    {
      "field": "document_home_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_formal_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_other",
      "show": false,
      "required": false
    },
  ],
  "institution_id": "45",
  "start_at": "2020-06-09 08:29:00",
  "finish_at": "2020-06-09 08:29:00",
}
```

**Success Response**
```json
{
  "id": "5f748a35f3d8b02e44b25f05",
  "uuid": "123e4567-e89b-12d3-a456-426614174000",//uuidv4
  "name": "PPDB Jalur Zonasi",//max: 100
  "description": null,//null or html string, max: 65000
  "thumbnail_id": null,//null or string, max: 500
  "thumbnail": null,//null or object
  "status": "active",//active, inactive
  "max_formulirs": null, //null or integer, min: 1, max: 5000
  "total_remaining_formulirs": 55, //default 0
  "total_capacities": null, //null or integer, min: 1, max: 5000
  "show_max_formulir": false,
  "show_remaining_formulir": false,
  "show_approval_at": "2020-06-09 08:29:00",//null or date
  "total_schools": 1,
  "schools": [
    {
      "id": "5f748a35f3d8b02e44b25f05",
      "name": "EDU SCHOOL",
      "logo": "https://image.png"
    }
  ],
  "formulir_settings": [
    {
      "field": "citizen_national_identifier", //nik
      "show": false,
      "required": false
    },
    {
      "field": "name",
      "show": true,
      "required": true
    },
    {
      "field": "gender",
      "show": false,
      "required": false
    },
    {
      "field": "birth_place",
      "show": false,
      "required": false
    },
    {
      "field": "birth_at",
      "show": false,
      "required": false,
      "range": { //object or null
        "minimum_total_days": 5000,//null or integer, min: 1
        "maximum_total_days": 6570,//null or integer, min: 1
        "date": "2001-01-01"
      }
    },
    {
      "field": "phone",
      "show": false,
      "required": false
    },
    {
      "field": "email",
      "show": false,
      "required": false
    },
    {
      "field": "photo",
      "show": false,
      "required": false
    },
    {
      "field": "achievement",
      "show": false,
      "required": false
    },
    {
      "field": "address",
      "show": false,
      "required": false,
      "zonation": { //object or null
        "villages": [
          {
            "id" : "6052fd0b2db1312c687892ef",
            "name" : "Bandung Kulon"
          }
        ]
      }
    },
    {
      "field": "school_national_identifier", //nisn
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_name",
      "show": false,
      "required": false
    },
    {
      "field": "institution_origin_identifier", //npsn
      "show": false,
      "required": false
    },
    {
      "field": "parent_name",
      "show": false,
      "required": false
    },
    {
      "field": "parent_gender",
      "show": false,
      "required": false
    },
    {
      "field": "parent_phone",
      "show": false,
      "required": false
    },
    {
      "field": "parent_email",
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_birth", //akta
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_family", //kk
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_good", //skck
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_domicile", //tinggal
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_healthy", //sehat
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_unable", //tidak mampu
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_electricity_bill", //rekening listrik
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_graduation",//skl
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_recommendation",//rekomendasi
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_responsibility_parent",//tanggung jawab orangtua wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_assignment_parent",//penugasan orangtua/wali
      "show": false,
      "required": false
    },
    {
      "field": "document_statement_registered_dtppfm",//Data Terpadu Program Penanganan Fakir Miskin
      "show": false,
      "required": false
    },
    {
      "field": "document_report_school",//rapor
      "show": false,
      "required": false
    },
    {
      "field": "document_certificate_school",//ijazah
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kks",//
      "show": false,
      "required": false
    },
    {
      "field": "document_card_pkh",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kip",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kis",
      "show": false,
      "required": false
    },
    {
      "field": "document_card_kbpnt",
      "show": false,
      "required": false
    },
    {
      "field": "document_home_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_formal_photo",
      "show": false,
      "required": false
    },
    {
      "field": "document_other",
      "show": false,
      "required": false
    },
  ],
  "institution_id": "45",
  "start_at": "2020-06-09 08:29:00",
  "finish_at": "2020-06-09 08:29:00",
  "created_at": "2020-06-09 08:29:00",
  "updated_at": "2020-06-09 08:29:00",
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "name",
			"message" : "Name should not greater than 100 character"
		}
	]
}
```

**Not found response**
```json
{
	"code": "404",
	"status": "NOT_FOUND",
	"message": "Resource not found"
}
```

**Error response**
```json
{
	"code": "400",
	"status": "ERROR",
	"message": "Error occured please try again later"
}
```

### Admission ownership
- Endpoint: **GET /v1/admission-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "admission_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_view": false, //should be true when user_id is instituton admin
    "status_update": false, //should be true when user_id is instituton admin.admission_management
    "status_delete": false, //should be true when user_id is instituton admin.admission_management
    "status_enroll": false //should be true when user_id is allowed to take formulirs
  }
}
```

---

### Admission authorization
- Endpoint: **GET /v1/admission-authorization**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "institution_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_create": false, //should be true when user_id is instituton admin.admission_management
  }
}
```

---

### Toggle admission status
- Endpoint: **POST /v1/admission/:identifier/toggle-status**
- Status: ☑️

**Success Response**
```json
{
	"code": "200",
	"status": "SUCCESS",
	"message": "Success toggle admission status"
}
```

**Not found response**
```json
{
	"code": "404",
	"status": "NOT_FOUND",
	"message": "Resource not found"
}
```

**Error response**
```json
{
	"code": "400",
	"status": "ERROR",
	"message": "Error occured please try again later"
}
```

### Statistic admission
- Endpoint: **GET /v1/admission-statistic**
- Status: ✋

**Success Response**
```json
{
	"code": "200",
	"status": "SUCCESS",
	"message": "Success",
  "data" : {
    "total_institutions" : 1000,
    "total_parents" : 1000,
    "total_students" : 1000,
    "total_admissions" : 1000,
    "total_available_formulirs" : 1000,
    "total_register_formulirs" : 1000,
  }
}
```

**Error response**
```json
{
	"code": "400",
	"status": "ERROR",
	"message": "Error occured please try again later"
}
```

### Statistic approval admission
- Endpoint: **GET /v1/admission-approval-statistic**
- Status: ✋

**Request Query**
```json
{
  "institution_id": 1
}
```

**Success Response**
```json
{
	"code": "200",
	"status": "SUCCESS",
	"message": "Success",
  "data" : {
    "total_registrants" : 1000,
    "total_capacities" : 1000,
    "total_unprocess" : 1000,
    "total_rejecteds" : 1000,
    "total_approvals" : 1000,
    "nearest_distances" : 1000,
    "fartest_distances" : 1000,
    "average_distances" : 1000
  }
}
```

**Error response**
```json
{
	"code": "400",
	"status": "ERROR",
	"message": "Error occured please try again later"
}
```

---

## Formulir
- [**1. Formulir list** | ☑️ ](#formulir-list)
- [**2. Formulir detail** | ☑️ ](#formulir-detail)
- [**3. Delete formulir** | ☑️ ](#delete-formulir)
- [**4. Check status** | ☑️ ](#check-status)
- [**5. Formulir enrollment** | ☑️ ](#formulir-enrollment)
- [**6. Formulir ownership** | ☑️ ](#formulir-ownership)
- [**7. Recover formulir** | ☑️ ](#recover-formulir)

- [**8. Update formulir identity** | ☑️ ](#update-formulir-identity)
- [**9. Update formulir address** | ☑️ ](#update-formulir-address) 
- [**10. Update formulir institution origin** | ☑️ ](#update-formulir-institution-origin)

- [**11. Create note** | ☑️ ](#create-note)
- [**12. Delete note** | ☑️ ](#delete-note)
- [**13. Note ownership** | ☑️ ](#Note-ownership)

- [**14. Create formulir document** | ☑️ ](#create-formulir-document)
- [**15. Delete formulir document** | ☑️ ](#delete-formulir-document)
- [**16. Formulir document ownership** | ☑️ ](#formulir-document-ownership)

- [**17. Create formulir parent** | ☑️ ](#create-formulir-parent)
- [**18. Update formulir parent** | ☑️ ](#update-formulir-parent)
- [**19. Delete formulir parent** | ☑️ ](#delete-formulir-parent)
- [**20. Formulir parent ownership** | ☑️ ](#formulir-parent-ownership)

- [**21. Create formulir achievement** | ☑️ ](#create-formulir-achievement)
- [**22. Update formulir achievement** | ☑️ ](#update-formulir-achievement)
- [**23. Delete formulir achievement** | ☑️ ](#delete-formulir-achievement)
- [**24. Formulir achievement ownership** | ☑️ ](#formulir-achievement-ownership)
- [**25. Update formulir achievement score** | ☑️ ](#update-formulir-achievement-score)

- [**26. Create formulir achievement document** | ☑️ ](#create-formulir-achievement-document)
- [**27. Delete formulir achievement document** | ☑️ ](#create-formulir-achievement-document)
- [**28. Formulir achievement document ownership** | ☑️ ](#formulir-achievement-document-ownership)

---

### Formulir list
- Endpoint: **GET /v1/formulir**
- Status: ☑️

**Request Query**
```json
{
  "admission_id": "5f748a35f3d8b02e44b25f05",
  "institution_id": "5f748a35f3d8b02e44b25f05",
  "school_id": "5f748a35f3d8b02e44b25f05",
  "user_id": "5f748a35f3d8b02e44b25f05",
  "status_verification": "invalid",
  "status_approval": "unapproved",
  "is_deleted": true,
  "limit": 300,
  "offset": 0,
  "q": "john",
  "sorts": [
    {
      "criteria": "birth_at", //birth_at, created_at, distance, achievement,
      "type": "asc" //asc, desc
    },
    {
      "criteria": "created_at",
      "type": "desc"
    }
  ],
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ping success",
  "data": {
    "total_pages": 1,
    "items": [
      {
        "id": "6061a1c640cc16759ef770fd",
        "uuid": "123e4567-e89b-12d3-a456-426614174000",
        "code": "16143128824940192",
        "status_verification": "valid",
        "status_approval": "unapproved",
        "formated_status_verification": "Valid",
        "formated_status_approval": "Tidak diterima",
        "admission": {
            "name": "PPDB Jalur Zonasi"
        },
        "institution": {
            "id": "6053243b25461f1fd43a8799",
            "name": "Dinas Kota Bandung",
            "logo": "https://i.picsum.photos/id/744/200/200.jpg?hmac=8T0b9ya-1hs9mQn1Sosud4eldJZ6haGcupAiLTJHe2o"
        },
        "schools": [
            {
                "school": {
                    "id": "6053246b25461f1fd43a879b",
                    "name": "Sekolah Test",
                    "logo": "https://i.picsum.photos/id/744/200/200.jpg?hmac=8T0b9ya-1hs9mQn1Sosud4eldJZ6haGcupAiLTJHe2o"
                },
                "total_distances": null
            }
        ],
        "identity": {
            "name": "Faisal Ihsanul Fikri, S.Kom",
            "birth_at": "1990-01-01"
        },
        "total_achievement_scores": 0,
        "notes": [
            {
                "message": "XYZ wkwkwk.",
                "user_name": "Idaman Indonesia",
                "created_at": "2021-04-19T06:05:48.268Z",
                "id": "607d1dbc0654e135f0dd7c64"
            },
            {
                "message": "XYZ wkwkwk.",
                "user_name": "Idaman Indonesia",
                "created_at": "2021-04-19T06:07:24.365Z",
                "id": "607d1e1c0654e135f0dd7c68"
            }
        ],
        "approved_in": null,
        "created_at": "2020-06-08T01:29:00.000Z"
      }
    ]
  }
}
```

---

### Formulir detail
- Endpoint: **GET /v1/formulir/:identifier**
- Status: ☑️

[**Object Formulir**](https://gitlab.com/edulogy/data/admission.md#formulir)

**Request Query**
```json
{
  "show_original_approval_status": false,
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ping success",
  "data": {
    // Formulir
  }
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

### Delete formulir
- Endpoint: **DELETE /v1/formulir/:identifier**
- Status: ☑️

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete formulir"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Check status
- Endpoint: **POST /v1/formulir-status**
- Status: ☑️

**Request Body**
```json
{
  "code" : "xxx",
  "token" : "12345abc"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "id": "5f748a35f3d8b02e44b25f05",
    "uuid": "123e4567-e89b-12d3-a456-426614174000",//uuidv4
    "code": "16143128824940192",
    "token": "hie758",
    "status_verification": "unprocess", //[unprocess, invalid, valid]
    "status_approval": "unapproved", //[unprocess, unapproved, approved]
    "formated_status_verification": "Belum diproses", //[unprocess, invalid, valid]
    "formated_status_approval": "Diterima", //[unprocess, unapproved, approved]
    "admission": {
      "id": "5f748a35f3d8b02e44b25f05",
      "uuid": "123e4567-e89b-12d3-a456-426614174000",
      "name": "Prestasi",
    },
    "institution": {
      "id": 1,
      "name": "Dinas Kota Bandung",
      "logo": "https://image.png"
    },
    "schools": [
      {
        "school": {
          "id": 45,
          "name": "EduOffice",
          "logo": "https://image.png"
        },
        "total_distances": 1000,
      }
    ],
    "identity" : {
      "name": "john"
    },
    "approved_in": {
      "id": "6053246b25461f1fd43a879b",
      "name": "Sekolah Test",
      "logo": "https://static.storage.edulogy.id/edulogy/edulogy-logo.png"
    }
  }
}
```

**Forbidden Response**
```json
{
  "code": "403",
  "status": "FORBIDDEN",
  "message": "You're not allowed get this resource"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "code",
			"message" : "Invalid code"
		}
		{
			"field" : "token",
			"message" : "Invalid token"
		}
	]
}
```

---

### Formulir enrollment
- Endpoint: **POST /v1/formulir-enrollment**
- Status: ☑️

**Request Body**
```json
{

  "admission_id": "6048451a23423c02c9ed1bba",
  "user_id": "6052e666281eb0397c6472e2",
  "school_ids": [
    "5f748a35f3d8b02e44b25f05",
    "5f748a35f3d8b02e44b25f05"
  ],
  "citizen_national_identifier": "id",//NIK
  "school_national_identifier": "id", //NISN
  "name": "john",
  "gender": "M",
  "birth_regency_name": "Bandung", //null or string
  "birth_at": "1990-01-01",
  "phone": "087825720207", //ke db harus 62
  "email": "john@edulogy.id",
  "photo_id": "5f748a35f3d8b02e44b25f05",
  "address": {    
    "country_id": "5f748a35f3d8b02e44b25f05",
    "province_id": "5f748a35f3d8b02e44b25f05",
    "regency_id": "5f748a35f3d8b02e44b25f05",
    "district_id": "5f748a35f3d8b02e44b25f05",
    "village_id": "5f748a35f3d8b02e44b25f05",
    "postal_code": "403222",
    "latitude": "102.32",
    "longitude": "42.32",
    "hamlet_number": "01",//rt
    "neighbourhood_number": "03",//rw
    "street": null
  },

  "institution_origin": {
    "name": "SDN 7 Bandung",
    "identifier": "7584748347", //npsn
  },

  "achievements": [
    {
      "name": "Juara 1 Lomba Makan Kerupuk",
      "description": null,
      "type": "sport",// [sport, art, academic, religion, other]
      "category": "team", // [individual, team]
      "rank": "international", //[international, asia, asean, national, province, regency]
      "position": "1st_winner", //['1st_winner','2nd_winner','3rd_winner','1st_runnerup','2nd_runnerup','3rd_runnerup','1_juz','2_juz','3_juz','other']
      "organizer_type": "kemenpora", //['other','kemendikbud','kemenag','kemenpora']
      "organizer_name": null, //required if type: other
      "documents": [
        {
          "attachment_id": "5f748a35f3d8b02e44b25f05"
        }
      ]
    }
  ],

  "parents": [
    {
      "type": "vice", //mother, father, vice //required
      "name": "Meow Meow",
      "gender": "M",
      "phone": "0872828282",
      "email": "parent@edulogy.id"
    }
  ],
  
  "documents": [
    {
      "document_type": "document_formal_photo",//document_formal_photo,document_certificate_birth,document_certificate_famil,,document_statement_good,document_statement_domicile,document_statement_healthy,document_statement_unabl,,document_statement_electricity_bill,document_statement_graduation,document_statement_recommendatio,,document_statement_responsibility_parent,document_statement_assignment_parent,document_statement_registered_dtppf,,document_report_school,document_certificate_school,document_card_kks,document_card_pkh,document_card_kip,document_card_ki,,document_card_kbpnt,document_home_photo,document_other
      "achievement_id": "123e4567"
    }
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "id": "5f748a35f3d8b02e44b25f05",
    "uuid": "123e4567-e89b-12d3-a456-426614174000",//uuidv4
    "code": "16143128824940192",
    "token": "hie758",
    "status_verification": "unprocess", //[unprocess, invalid, valid]
    "status_approval": "unapproved", //[unprocess, unapproved, approved]
    "formated_status_verification": "Belum diproses", //[unprocess, invalid, valid]
    "formated_status_approval": "Diterima", //[unprocess, unapproved, approved]
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "nationality_id",
			"message" : "Invalid nationality_id"
		}
	]
}
```

---

### Formulir ownership
- Endpoint: **GET /v1/formulir-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "formulir_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_view": false, //should be true when user_id is formulir.owner or user_id is institution.admin.verificators or institution.admin.approvals
    "status_update": false, //should be true when user_id is formulir.owner and status_verification = unprocess or invalid
    "status_delete": false, //should be true when user_id is admin in formulir.institution
    "status_create_note": false //should be true when user_id is admin.admission_management in formulir.institution
  }
}
```

---

### Recover formulir
- Endpoint: **POST /v1/formulir-recover**
- Status: ☑️ 

**Request Body**
```json
{
  "formulir_ids": [

  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "success"
}
```

---

### Update formulir identity
- Endpoint: **PUT /v1/formulir-identity**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05",
  "modifier_id": "6052e666281eb0397c6472e2",
  "citizen_national_identifier": "id",//NIK
  "school_national_identifier": "id", //NISN
  "certificate_number": "840725", //no ijazah
  "name": "john",
  "gender": "M",
  "birth_regency_name": "Bandung", //null or string
  "birth_at": "1990-01-01",
  "phone": "087825720207",
  "email": "john@edulogy.id",
  "photo_id": "6052e666281eb0397c6472e2",
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir identity"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "email",
			"message" : "Invalid email"
		}
	]
}
```

---

### Update formulir address
- Endpoint: **PUT /v1/formulir-address**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05", 
  "modifier_id": "6052e666281eb0397c6472e2",
  "country_id": "5f748a35f3d8b02e44b25f05",
  "province_id": "5f748a35f3d8b02e44b25f05",
  "regency_id": "5f748a35f3d8b02e44b25f05",
  "district_id": "5f748a35f3d8b02e44b25f05",
  "village_id": "5f748a35f3d8b02e44b25f05",
  "postal_code": "403222",
  "latitude": 102.32,
  "longitude": 42.32,
  "hamlet_number": "01",//rt
  "neighbourhood_number": "03",//rw
  "street": null
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir address"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "country_id",
			"message" : "Invalid country_id"
		}
	]
}
```

---

### Update formulir institution origin
- Endpoint: **PUT /v1/formulir-institution-origin**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05",
  "modifier_id": "6052e666281eb0397c6472e2",
  "name": "SDN 7 Bandung",
  "identifier": "7584748347", //npsn
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir institution origin"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "country_id",
			"message" : "Invalid country_id"
		}
	]
}
```

### Create note
- Endpoint: **POST /v1/formulir-note**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "6061a1c640cc16759ef770fd",
  "modifier_id": "6052e666281eb0397c6472e2",
  "user_id": "6061a1c640cc16759ef770fd",
  "message": "Mohon lengkapi data KTP orangtuanya yaa.."
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success create note"
}
```

---

### Delete note
- Endpoint: **DELETE /v1/formulir-note/:identifier**
- Status: ☑️

**Request body**
```json
{
  "modifier_id": "6052e666281eb0397c6472e2"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete note"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Note ownership
- Endpoint: **GET /v1/formulir-note-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "note_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_delete": false, //should be true when user_id is admin.admission_management in formulir.institution
  }
}
```

---

### Create formulir document
- Endpoint: **POST /v1/formulir-document**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05",
  "modifier_id": "6052e666281eb0397c6472e2",
  "documents": [
    {
      "document_type": "formal_photo",//certificate_birth, certificate_family, statement_good, statement_domicile, statement_healthy, statement_unable, statement_electricity_bill, statement_graduation, statement_recommendation, statement_responsibility_parent, statement_assignment_parent, statement_registered_dtppfm, report_school, certificate_school, card_kks, card_pkh, card_kip, card_kis, card_kbpnt, home_photo, other
      "attachment_id": "123e4567"
    }
  ],
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success create documents"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "documents[0].document_type",
			"message" : "Invalid documents[0].document_type"
		}
	]
}
```

---

### Delete formulir document
- Endpoint: **DELETE /v1/formulir-document/:id**
- Status: ☑️

**Request body**
```json
{
  "modifier_id": "6052e666281eb0397c6472e2"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete document"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Formulir document ownership
- Endpoint: **GET /v1/formulir-document-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "document_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_delete": false, //should be true when user_id is owner of ther formulir
  }
}
```

---

### Create formulir parent
- Endpoint: **POST /v1/formulir-parent**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05",
  "type": "vice", //mother, father, vice
  "name": "Meow Meow",
  "gender": "M",
  "phone": "0872828282",
  "email": "parent@edulogy.id",
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success create parents"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "religion_id",
			"message" : "Invalid religion_id"
		}
	]
}
```

---

### Update formulir parent
- Endpoint: **PUT /v1/formulir-parent/:id**
- Status: ☑️

**Request body**
```json
{
  "type": "vice", //mother, father, vice
  "name": "Meow Meow",
  "gender": "M",
  "phone": "0872828282",
  "email": "parent@edulogy.id",
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir parent"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "type",
			"message" : "Invalid type"
		}
	]
}
```

---

### Delete formulir parent
- Endpoint: **DELETE /v1/formulir-parent/:id**
- Status: ☑️

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete parent"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Formulir parent ownership
- Endpoint: **GET /v1/formulir-parent-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "parent_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_update": false, //should be true when user_id is owner of ther formulir
    "status_delete": false, //should be true when user_id is owner of ther formulir
  }
}
```

---

### Create formulir achievement
- Endpoint: **POST /v1/formulir-achievement**
- Status: ☑️

**Request body**
```json
{
  "formulir_id": "5f748a35f3d8b02e44b25f05",
  "name": "Juara 1 Lomba Makan Kerupuk",
  "description": null,
  "type": "sport",// [sport, art, academic, religion, other]
  "category": "team", // [individual, team]
  "rank": "international", //[international, asia, asean, national, province, regency]
  "position": "1st_winner", //['1st_winner','2nd_winner','3rd_winner','1st_runnerup','2nd_runnerup','3rd_runnerup','1_juz','2_juz','3_juz','other']
  "organizer_type": "kemenpora", //['other','kemendikbud','kemenag','kemenpora']
  "organizer_name": null, //required if type: other
  "documents": [
    {
      "file_id": "23"
    }
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success create achievement"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "rank",
			"message" : "Invalid rank"
		}
	]
}
```

---

### Update formulir achievement
- Endpoint: **PUT /v1/formulir-achievement/:id**
- Status: ☑️

**Request body**
```json
{
  "name": "Juara 1 Lomba Makan Kerupuk",
  "description": null,
  "type": "sport",// [sport, art, academic, religion, other]
  "category": "team", // [individual, team]
  "rank": "international", //[international, asia, asean, national, province, regency]
  "position": "1st_winner", //['1st_winner','2nd_winner','3rd_winner','1st_runnerup','2nd_runnerup','3rd_runnerup','1_juz','2_juz','3_juz','other']
  "organizer_type": "kemenpora", //['other','kemendikbud','kemenag','kemenpora']
  "organizer_name": null, //required if type: other
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir achievement"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "institution_origin.address.country_id",
			"message" : "Invalid institution_origin.address.country_id"
		}
	]
}
```

---

### Delete formulir achievement
- Endpoint: **DELETE /v1/formulir-achievement/:id**
- Status: ☑️

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete achievement"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Formulir achievement ownership
- Endpoint: **GET /v1/formulir-achievement-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "achievement_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_update": false, //should be true when user_id is owner of ther formulir
    "status_delete": false, //should be true when user_id is owner of ther formulir
    "status_update_score": false, //should be true when user_id is admin admission_approval in this institution
  }
}
```

---

### Update formulir achievement score
- Endpoint: **POST /v1/formulir-achievement-score/:id**
- Status: ☑️

**Request body**
```json
{
  "score": "30.52", //nullable
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update achievement score"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "score",
			"message" : "Invalid value"
		}
	]
}
```

---

### Create formulir achievement document
- Endpoint: **POST /v1/formulir-achievement-document**
- Status: ☑️

**Request body**
```json
{
  "formulir_achievement_id": "1avsbffv",
  "documents": [
    {
      "file_id": "23"
    }
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success create achievement document"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "documents[0].file_id",
			"message" : "Invalid documents[0].file_id"
		}
	]
}
```

---

### Delete formulir achievement document
- Endpoint: **DELETE /v1/formulir-achievement-document/:id**
- Status: ☑️

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success delete achievement document"
}
```

**Not found Response**
```json
{
  "code": "404",
  "status": "NOT_FOUND",
  "message": "resource not found"
}
```

---

### Formulir achievement document ownership
- Endpoint: **GET /v1/formulir-achievement-document-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "document_id" : "5f748a35f3d8b02e44b25f05"
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_delete": false, //should be true when user_id is owner of ther formulir
  }
}
```

---

## Formulir Status
- [**1. Update verification status** | ☑️ ](#update-verification-status)
- [**2. Send verification notification** | ☑️ ](#send-verification-notification)
- [**3. Update approval status** | ☑️ ](#update-approval-status)
- [**4. Send approval notification** | ☑️ ](#send-approval-notification)
- [**4. Formulir Status Ownership** | ☑️ ](#formulir-status-ownership)
- [**5. Statistik pendaftar** | ✋ ](#statistik-pendaftar)

### Update verification status
- Endpoint: **POST /v1/formulir-verification**
- Status: ☑️

**Request Body**
```json
{
  "formulirs": [
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_verification": "valid"
    },
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_verification": "invalid"
    },
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_verification": "unprocess"
    }
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir verification status"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "formulir_id[0]",
			"message" : "Formulir already proceed"
		}
	]
}
```

---

### Send verification notification
- Endpoint: **POST /v1/formulir-verification-notification**
- Status: ☑️

**Request Body**
```json
{
  "formulir_ids": [
    "5f748a35f3d8b02e44b25f05", "5f748a35f3d8b02e44b25f05"
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Notification is on the way"
}
```

---

### Update approval status
- Endpoint: **POST /v1/formulir-approval**
- Status: ☑️

**Request Body**
```json
{
  "formulirs": [
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_approval": "approved",
      "approved_id": "5f748a35f3d8b02e44b25f05",
    },
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_approval": "unapproved",
      "approved_id": "5f748a35f3d8b02e44b25f05",
    },
    {
      "formulir_id": "5f748a35f3d8b02e44b25f05",
      "status_approval": "unprocess",
      "approved_id": "5f748a35f3d8b02e44b25f05",
    }
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success update formulir approval status"
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "formulir_id[0]",
			"message" : "Formulir already proceed"
		}
	]
}
```

---

### Send approval notification
- Endpoint: **POST /v1/formulir-approval-notification**
- Status: ☑️

**Request Body**
```json
{
  "formulir_ids": [
    "5f748a35f3d8b02e44b25f05", "5f748a35f3d8b02e44b25f05"
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Notification is on the way"
}
```

---

### Formulir status ownership
- Endpoint: **GET /v1/formulir-status-ownership**
- Status: ☑️

**Request Query**
```json
{
  "user_id" : "5f748a35f3d8b02e44b25f05",
  "formulir_ids" : [
    "5f748a35f3d8b02e44b25f05"
  ]
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "Success",
  "data" : {
    "status_verification": false, //should be true when user_id is admin admission_verification.institution_ids in formulir's institution
    "status_approval": false, //should be true when user_id is admin admission_approval.institution_ids in formulir's institution
  }
}
```

---

### Statistik pendaftar
- Endpoint: **GET /v1/statistic-registration**
- Status: ✋

**Request Query**
```json
{
  "school_ids": [
    45, 19
  ], //optional
  "institution_id": 191//dinas
}
```

**Success Response**
```json
{
  "status": "success",
  "code": "00",
  "message": "Successfully connected",
  "data": {
    "distributions": [
      {
        "label": "Zonasi",
        "total_unprocess_formulirs": 425,
        "total_approved_formulirs": 425,
        "total_unapproved_formulirs": 42,
        "total_remaining_formulirs": 42222,
        "total_capacities": 0,
        "nearest_distances": 200,
        "fartest_distances": 202822,
        "average_distances": 113222,
      },
      {
        "label": "Afirmasi",
        "total_unprocess_formulirs": 425,
        "total_approved_formulirs": 425,
        "total_unapproved_formulirs": 42,
        "total_remaining_formulirs": 42222,
        "total_capacities": 0,
        "nearest_distances": 200,
        "fartest_distances": 202822,
        "average_distances": 113222,
      },
      {
        "label": "Prestasi",
        "total_unprocess_formulirs": 425,
        "total_approved_formulirs": 425,
        "total_unapproved_formulirs": 42,
        "total_remaining_formulirs": 42222,
        "total_capacities": 0,
        "nearest_distances": 200,
        "fartest_distances": 202822,
        "average_distances": 113222,
      },
      {
        "label": "Perpindahan Tugas Orang Tua",
        "total_unprocess_formulirs": 425,
        "total_approved_formulirs": 425,
        "total_unapproved_formulirs": 42,
        "total_remaining_formulirs": 42222,
        "total_capacities": 0,
        "nearest_distances": 200,
        "fartest_distances": 202822,
        "average_distances": 113222,
      }
    ]
  }
}
```

---

## Location
- [**1. Area detection** | ☑️ ](#area-detection)
- [**2. Distance calculation** | ☑️ ](#distance-calculation)

### Area detection
- Endpoint: **POST /v1/area-detection**
- Status: ☑️

**Request Body**
```json
{
  "latitude": -6.922314,
  "longitude": 107.69847630000001
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ok",
  "data": {
    "country": {
      "id": "6052d5011aa6db20ac9a39da",
      "name": "Indonesia",
      "latitude": -0.789275,
      "longitude": 113.9213257,
      "total_distances": 970127.744399777
    },
    "province": {
      "id": "6052d95cc02e6837a0e65f45",
      "name": "Jawa Barat",
      "latitude": -7.090911,
      "longitude": 107.668887,
      "total_distances": 19028.512167047025
    },
    "regency": {
      "id": "6052e95e6881f734101dcc80",
      "name": "Kota Bandung",
      "latitude": -6.9174639,
      "longitude": 107.6191228,
      "total_distances": 8775.595273862167
    },
    "district": {
      "id": "6052ef47014a1015a02f5402",
      "name": "Panyileukan",
      "latitude": -6.932218,
      "longitude": 107.7073688,
      "total_distances": 1475.1612846322644
    },
    "village": {
      "id": "6052fd0b2db1312c6878932b",
      "name": "Cipadung Kulon",
      "latitude": -6.922051,
      "longitude": 107.703451,
      "total_distances": 549.8809694757952
    },
    "postal_code": null
  }
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "latitude",
			"message" : "Invalid value"
		}
	]
}
```

---

### Distance calculation
- Endpoint: **POST /v1/distance-calculation**
- Status: ☑️

**Request Body**
```json
{
  "latitude1": -6.9174639,
  "longitude1": 107.6191228,
  "latitude2": -6.937520999999999,
  "longitude2": 107.67119439999999
}
```

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ok",
  "data": {
    "total_distances": 6165.052268284855,
    "formated_total_distances": "6,165 Meter"
  }
}
```

**Invalid data response**
```json
{
	"code": "422",
	"status": "INVALID DATA",
	"message": "Error",
	"error": [
		{
			"field" : "latitude",
			"message" : "Invalid value"
		}
	]
}
```

---

## Component
- [**1. Component map**       ✋ ](#component-map)

### Component map 
- Endpoint: **GET /v1/component-map**
- Status: ✋ 

**Success Response**
```json
{
  "code": "200",
  "status": "SUCCESS",
  "message": "ping success",
  "data": [
    {
      "id": 1,
      "name": "EduOffice",
      "logo": "https://edulogy.jpg",
      "latitude":-6.90400500,
      "longitude": 107.66740400,
      "street": "Jl. Jalan Saja No. 99",
      "slug": "SMK_AL_HADI",
      "grades":[
        "junior","senior"
      ],
      "category":"private",
      "type":"school"
    },
    {
      "id": 1,
      "name": "EduOffice",
      "logo": "https://edulogy.jpg",
      "latitude":-6.90400500,
      "longitude": 107.66740400,
      "street": "Jl. Jalan Saja No. 99",
      "slug": "SMK_AL_HADI",
      "grades":[
        "junior","senior"
      ],
      "category":"private",
      "type":"school"
    }
  ]
}
```

---

