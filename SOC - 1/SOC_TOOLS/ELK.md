# ELK

- `ELK` originally referred to just three components—Elasticsearch, Logstash, and Kibana. Once Beats were introduced, the stack is often called the Elastic Stack.

- These are three open-source tools that are commonly used together to collect, store, analyse, and visualise data.

- ELK --> USED FOR LOG ANALYSIS AND INVESTIGATION

- Explain each component behind `ELK` :
    - ` BEAT ` --> It collects data froom multiple agents
    - `LOGSTASH` --> collects data from beats, ports, or files, parses/normalizes it into field value pairs, and stores them into Elasticsearch.
    - `ELASTIC SEARCH` --> Acts as database to search and analyse data
    - `KIBANA` -->  responsible for displaying and visualizing the data stored in Elasticsearch. The data stored in Elasticsearch can easily be shaped into different visualizations, time charts, infographics, etc., using Kibana.


- ELK uses the query Language --> `KBL` [ ` KEBANA QUERY LANGUAGE `] 

- SEARCHING USING KBL :
    - ` USE FULL TERMS/WORDS `
    - `FOR SEARCHING EVERYTHING, USE WILDCARD OPERATOR *`
        - EX: ` UNITED * ` --> will give us everything starting from `united`
    - `LOGICAL OPERATORS`
        - `AND` --> ex :"us" AND "uk"
        - `OR ` --> ex : "us" OR "uk"
        - `NOT` --> ex : "us" NOT ("India")
    - `FIELD BASED SEARCH`
        - This has special syntax : ` Field: Value `
            - EX : `Source_ip : 238.163.231.224 AND UserName : Suleman`


-- DOONE