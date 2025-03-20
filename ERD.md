```mermaid
erDiagram
    WARD {
        string WardName PK
        int TotalPatients
    }

    PATIENT {
        string MRN PK
        string Name
        string Address_City
        string Address_Street
        string Address_Code
        string PhoneNumbers
        datetime AdmissionDateTime
        string WardName FK
        string ConsultantName FK
    }

    CONSULTANT {
        string Name PK
        string Specialization
    }

    TEST {
        string EpisodeNo PK
        string Category
        string Result
        string ConsultantName FK
    }

    TEST_RECORD {
        string TestRecordID PK
        string MRN FK
        string EpisodeNo FK
        datetime TestDate
    }

    WARD ||--o{ PATIENT : "has"
    WARD ||--o{ CONSULTANT : "specializes in"
    CONSULTANT ||--o{ PATIENT : "leads"
    PATIENT ||--o{ TEST_RECORD : "undergoes"
    TEST ||--o{ TEST_RECORD : "includes"
    CONSULTANT ||--o{ TEST : "orders"
