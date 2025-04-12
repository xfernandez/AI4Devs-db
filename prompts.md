- Actua como software developer especializado en Datos y bases de datos. Primero de todo, revisa todo el proyecto y hazme un primer resumen

- Nos han pedido evolucionar el esquema. Te comparto el esquema ERD completo para que me detectes las diferencias con el esquema inicial y me generes los cambios de base de datos. Tómate el tiempo que sea necesario y hazme preguntas si crees importante. Es importante que sigas las buenas prácticas de normalización para tener alta escalabilidad y evalues la incorporación de índices que mejoren el rendimiento de la base de datos.
erDiagram
     COMPANY {
         int id PK
         string name
     }
     EMPLOYEE {
         int id PK
         int company_id FK
         string name
         string email
         string role
         boolean is_active
     }
     POSITION {
         int id PK
         int company_id FK
         int interview_flow_id FK
         string title
         text description
         string status
         boolean is_visible
         string location
         text job_description
         text requirements
         text responsibilities
         numeric salary_min
         numeric salary_max
         string employment_type
         text benefits
         text company_description
         date application_deadline
         string contact_info
     }
     INTERVIEW_FLOW {
         int id PK
         string description
     }
     INTERVIEW_STEP {
         int id PK
         int interview_flow_id FK
         int interview_type_id FK
         string name
         int order_index
     }
     INTERVIEW_TYPE {
         int id PK
         string name
         text description
     }
     CANDIDATE {
         int id PK
         string firstName
         string lastName
         string email
         string phone
         string address
     }
     APPLICATION {
         int id PK
         int position_id FK
         int candidate_id FK
         date application_date
         string status
         text notes
     }
     INTERVIEW {
         int id PK
         int application_id FK
         int interview_step_id FK
         int employee_id FK
         date interview_date
         string result
         int score
         text notes
     }

     COMPANY ||--o{ EMPLOYEE : employs
     COMPANY ||--o{ POSITION : offers
     POSITION ||--|| INTERVIEW_FLOW : assigns
     INTERVIEW_FLOW ||--o{ INTERVIEW_STEP : contains
     INTERVIEW_STEP ||--|| INTERVIEW_TYPE : uses
     POSITION ||--o{ APPLICATION : receives
     CANDIDATE ||--o{ APPLICATION : submits
     APPLICATION ||--o{ INTERVIEW : has
     INTERVIEW ||--|| INTERVIEW_STEP : consists_of
     EMPLOYEE ||--o{ INTERVIEW : conducts

- No hagamos ningun cambio, quiero que vuelvas a analizar lo que te he pasado son las nuevas entidades que se deben de incorporar. No es ninguna diferencia     


- Vale, para dar por cerrada la tarea, tomate el tiempo que creas necesario para verificar la base de datos. 
Comprobar que todas las tablas se han creado correctamente
Verificar que los índices están en su lugar
Confirmar que las relaciones funcionan como se espera