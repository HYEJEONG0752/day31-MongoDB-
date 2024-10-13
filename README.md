# Day4: MongoDB 활용 과제

# MongoDB 기초 및 개념

1. **MongoDB는 어떤 유형의 데이터베이스이며, 어떤 형식으로 데이터를 저장합니까? MongoDB의 스키마 특성에 대해 설명하세요.**
    - NoSQL 데이터베이스의 일종으로, 문서 지향 데이터베이스입니다.
    - MongoDB의 데이터 저장 형식 :
        1) 문서 : MongoDB의 기본 데이터 단위로, 키-값 쌍의 집합입니다. 각 문서는 고유한 `_id`필드를 가지며, JSON 형식으로 표현됩니다.
        2) 컬렉션 : 문서의 집합으로, 관계형 데이터베이스의 테이블에 해당합니다. 컬렉션은 스키마가 없는 구조를 가집니다.
    - MongoDB의 스키마 특성 :
        1) 스키마 유연성 : MongoDB는 스키마가 없는 데이터베이스입니다. 즉, 문서는 서로 다른 구조를 가질 수 있으며, 동일한 컬렉션 내의 문서들이 서로 다른 필드를 가질 수 있습니다. 이는 데이터 모델링에 유연성을 제공합니다.
        2) 동적 스키마 : 데이터 구조를 사전에 정의할 필요가 없으며, 필요에 따라 필드를 추가하거나 변경할 수 있습니다. 이는 애플리케이션의 요구 사항이 변화할 때 유용합니다.
        3) 중첩된 데이터 구조 : MongoDB는 문서 내에 배열이나 다른 문서를 중첩하여 저장할 수 있습니다. 이를 통해 복잡한 데이터 구조를 자연스럽게 표현할 수 있습니다.
        4) 데이터 타입 지원 : MongoDB는 다양한 데이터 타입을 지원합니다. 문자열, 숫자, 날짜, 배열, 객체 등 다양한 형식의 데이터를 저장할 수 있습니다.
        5) 인덱싱 : MongoDB는 인덱스를 사용하여 쿼리 성능을 향상시킬 수 있습니다. 기본적으로 `_id`필드에 인덱스가 생성되며, 추가적인 인덱스를 생성하여 특정 필드에 대한 검색 성능을 개선할 수 있습니다.

2. **MongoDB에서 문서(Document)와 컬렉션(Collection)의 개념을 설명하고, SQL에서 테이블(Table)과의 차이점을 비교하세요.**
    - 문서(Document) : MongoDB에서 문서는 JSON과 유사한 BSON 형식으로 저장되는 데이터의 기본 단위입니다. 각 문서는 키-값 쌍으로 구성되며, 다양한 데이터타입을 포합할 수 있습니다.
    - 컬렉션(Collection) : 컬렉션은 문서의 집합으로, SQL의 테이블에 해당합니다. 컬렉션은 특정한 스키마를 요구하지 않으며, 서로 다른 구조의 문서들을 포함할 수 있습니다.
    - 차이점 :
        1) 스키마: SQL테이블은 사전에 정의된 스키마를 가지며, 모든 행이 동일한 구조를 가져야 합니다. 반면, MongoDB의 컬렉션은 스키마가 없어 각 문서가 서로 다른 구조를 가질 수 있습니다.
        2) 데이터 형식 : SQL은 정형 데이터(테이블 형식)만을 지원하는 반면, MongoDB는 비정형 및 반정형 데이터를 지원합니다.
        3) 관계 : SQL은 관계형 데이터베이스로, 테이블 간의 관계를 정의할 수 있습니다. MongoDB는 문서 간의 관계를 중첩된 문서나 배열을 통해 표현할 수 있지만, 전통적인 관계형 모델과는 다릅니다.

3. **MongoDB에서 스키마리스(Schemaless) 데이터베이스의 장점과 단점을 설명하세요.**
    - 장점
        1) 유연성 : 데이터 구조를 사전에 정의할 필요가 없어, 애플리케이션의 요구 사항 변화에 쉽게 대응할 수 있습니다.
        2) 빠른 개발 : 개발 초기 단계에서 데이터 모델을 자주 변경할 수 있어, 프로토타입 개발 및 반복적인 개발에 유리합니다.
        3) 다양한 데이터 형식 지원 : 서로 다른 형식의 데이터를 동일한 컬렉션에 저장할 수 있어, 다양한 데이터 소스를 통합하기 용이합니다.
    - 단점
        1) 데이터 일관성 문제 : 스키마가 없기 때문에, 데이터의 일관성을 유지하기 어려울 수 있습니다. 잘못된 데이터 형식이 저장될 위험이 있습니다.
        2) 쿼리 복잡성 : 데이터 구조가 다양해질수록 쿼리가 복잡해질 수 있으며, 데이터의 구조를 이해하는 데 추가적인 노력이 필요합니다.
        3) 성능 저하 : 비정형 데이터가 많아질 경우, 인덱스 최적화가 어려워져 성능이 저하될 수 있습니다.

4. **MongoDB의 주요 특징 중 수평적 확장성에 대해 설명하고, 샤딩(Sharding)이 어떻게 수평적 확장을 지원하는지 서술하세요.**
    - 수평적 확장성 : 데이터베이스가 증가하는 데이터 양과 트래픽을 처리하기 위해 여러 서버에 걸쳐 데이터를 분산할 수 있는 능력을 의미합니다.
        수평적 확장성은 시스템의 성능을 향상시키고, 더 많은 사용자를 지원할 수 있도록 해줍니다. 
        이는 수직적 확장성(서버의 성능을 높이는 것)과는 달리, 여러 대의 서버를 추가하여 시스템의 용량을 늘리는 방식입니다.
    - 샤딩이 수평적 확장을 지원하는 방식
        1) 데이터 분산 : 데이터를 여러 샤드에 분산하여 저장합니다.
        2) 샤딩 키 : 데이터를 어떻게 분산할지를 결정하는 기준이 되는 필드로, 키를 기반으로 MongoDB는 데이터를 특정샤드에 할당합니다.
        3) 쿼리 라우팅 : 클라이언트의 요청은 쿼리라우터를 통해 적절한 샤드로 전달됩니다.
        4) 부하 분산 : 샤딩을 통해 데이터와 요청이 여러 서버에 분산되므로, 특정 샤드에 트래픽이 집중되지 않습니다.
        5) 확장성 : 데이터베이스의 용량이나 성능이 부족할 경우, 새로운 서버를 추가하고 기존 데이터의 일부를 새로운 샤드로 재분배함으로써 시스템을 확장할 수 있습니다.
        6) 고가용성 및 내결함성 : 샤딩은 데이터의 복제본을 여러 샤드에 저장할 수 있는 기능과 결합되어, 데이터의 가용성을 높입니다.
        만약 하나의 샤드가 실패하더라도 다른 샤드에서 데이터를 계속 사용할 수 있습니다.
        7) 성능 최적화 : 각 샤드는 독립적으로 쿼리를 처리할 수 있기 때문에, 데이터베이스의 성능이 향상됩니다.

5. **MongoDB에서 BSON(Binary JSON) 형식이 사용되는 이유와 이 형식의 주요 특징에 대해 설명하세요.**
    - 이유 : BSON은 이진 형식으로 데이터를 저장하므로, JSON보다 저 작은 크기로 데이터를 표현할 수 있어 효율적인 저장이 가능하머,
    데이터의 직렬화 및 역직렬화가 가능해 빠른 데이터 접근이 가능합니다.
    -  BSON 특징 : 
        1) 이진형식 : 이진형식으로 데이터를 표현하여, JSON보다 더 빠르고 효율적으로 데이터를 처리할 수 있습니다.
        2) 다양한 데이터 타입 : 기본 타입(문자열, 정수, 부동 소수점, 불리언, null), 복합타입(배열, 객체), 특수 타입(날짜, ObjectId 등)
        3) 크기 정보 포함 : 각 필드의 크기를 포함하고 있어, 데이터의 크기를 쉽게 계산할 수 있습니다.
        4) 계층적 구조 : 중첩된 문서와 배열을 지원하여, 복잡한 데이터 구조를 표현할 수 있습니다.
        5) 인덱싱 지원 : MongoDB의 인덱싱 기능과 잘 통합되어 있어, 효율적인 쿼리 성능을 제공합니다.
        5) 호환성 : JSON과 호환성이 있어, JSON형식으로 데이터를 쉽게 변환할 수 있고 이로 인해 다른 시스템과의 데이터 교환을 용이하게 합니다.
---

# MongoDB 트랜잭션 관련

1. **MongoDB에서 멀티 도큐먼트 트랜잭션(Multi-Document Transaction)이 무엇이며, 어떻게 작동하는지 설명하세요.**
    - MongoDB에서 여러 도큐먼트에 걸쳐 원자적으로 작업을 수행할 수 있는 기능입니다.
    - 트랜잭션을 시작하면, MongoDB는 해당 트랜잭션에 대한 컨텍스트를 생성하고, 여러 도큐먼트에 대한 읽기 및 쓰기 작업을 수행할 수 있습니다.
    모든 작업이 완료되면 `commitTransaction()`메서드를 호출하여 변경사항을 저장하고, 중간에 오류가 생기면 `abortTransaction()`메서드를 호출하여 모든 변경사항을 콜백합니다.

2. **MongoDB 트랜잭션의 ACID 속성(Atomicity, Consistency, Isolation, Durability)에 대해 설명하고, 각 속성이 트랜잭션에서 어떤 역할을 하는지 서술하세요.**
    - Atomicity(원자성) : 트랜잭션 내의 모든 작업이 성공적으로 완료되거나, 하나라도 실패하면 모든 작업이 취소됩니다. 
    - Consistency(일관성) : 트랜잭션이 완료되면 데이터베이스는 항상 일관된 상태로 유지됩니다.
    - Isolation(격리성) : 각 트랜잭션은 독립적으로 실행되며, 다른 트랜잭션이 중간 상태를 볼 수 없습니다.
    - Durability(지속성) : 트랜잭션이 성공적으로 완료되면, 그 결과는 영구적으로 데이터베이스에 저장됩니다.

3. **MongoDB 트랜잭션 사용 시, 데이터 일관성을 보장하기 위해 사용하는 `commitTransaction()`과 `abortTransaction()` 메서드의 역할을 설명하세요.**
    - `commitTransaction()` : 트랜잭션 내에서 수행된 모든 변경 사항을 데이터베이스에 영구적으로 저장합니다.
    이 메서드가 호출되면 트랜잭션이 성공적으로 완료되었다고 간주됩니다.
    - `abortTransaction()` : 트랜잭션 내에서 수행된 모든 변경 사항을 취소하고, 데이터베이스를 트랜잭션 시작 전의 상태로 되돌립니다. 
    이 메서드는 오류가 발생했거나, 트랜잭션을 더 이상 진행할 수 없을 때 호출됩니다.

4. **MongoDB에서 트랜잭션을 사용할 수 있는 환경을 설명하고, 단일 인스턴스에서 트랜잭션이 가능한지 여부를 기술하세요.**
    - Replica Set 또는 sharded cluster 환경이 필요합니다.
    - 단일 인스턴스에서는 트랜잭션을 사용할 수 없습니다. 반드시 Replica Set환경에서만 멀티 도큐먼트 트랜잭션을 사용할 수 있습니다.

5. **MongoDB에서 트랜잭션을 구현한 예시 코드를 제시하고, 각 단계별로 동작 방식을 설명하세요.**
    ```jsx
    import {MongoClient} from 'mongodb';

    const uri = 'mongodb://localhost:27017';    //MongoDB 연결 URI
    const client = new MongoClient(uri);

    async function runTransaction() {
        const session = client.startSession();  // 트랜잭션을 시작할 세션 생성
        const userCollection = client.db('bank').Collection('users');
        const accountsCollection = client.db('bank').Collection('accounts');

        // 트랜잭션 시작
        session.startTransaction();

        try {
            //Step1: 송금자 계좌에서 100$ 차감
            await accountsCollection.updateOne(
                {accountId: '12345'}, // 송금자 계좌 ID
                {$inc: { balance: -100 }},  // 잔약 100$차감
                {session}   // 트랜잭션 세션 사용
            );

            //Step2: 수신자 계좌에 100$ 추가
            await accountsCollection.updateOne(
                {accountId: '67890'},   //수신자 계좌 ID
                {$inc: { balance: 100}},    // 잔액 100$ 추가
                {session}   // 트랜잭션 세션 사용
            );

            // 트랜잭션 커밋(성공 시)
            await session.commitTransaction();
            console.log('Transaction succesfully committed.');
        } catch (error) {
            // 오류 발생 시 트랜잭션 롤백
            await session.abortTransaction();
            console.error('Transaction aborted due to an error: ', error);
        } finally {
            // 세션 종료
            session.endSession();
            await client.close();
        }
    }

    runTransaction().catch(console.error);
    ```
    1. MongoClient 및 세션 생성: `MongoClient`를 사용하여 MongoDB에 연결하고, 트랜잭션을 처리할 세션을 생성합니다.
    2. 트랜잭션 시작: `session.startTransaction()` 메서드를 통해 트랜잭션을 시작합니다.
    3. 업데이트 작업 수행:
        - 첫 번째 `updateOne()`에서는 송금자의 계좌에서 100달러를 차감하고, 두 번째 `updateOne()`에서는 수신자의 계좌에 100달러를 추가합니다.
        - 두 작업 모두 동일한 트랜잭션 세션 내에서 처리되므로, 둘 중 하나라도 실패하면 전체 트랜잭션이 롤백됩니다.
    4. 트랜잭션 커밋: 모든 작업이 성공적으로 완료되면 `session.commitTransaction()`을 호출하여 트랜잭션을 커밋합니다.
    5. 트랜잭션 롤백: 만약 작업 중 오류가 발생하면, `session.abortTransaction()`을 호출하여 트랜잭션을 취소하고 롤백합니다.
    6. 세션 종료: 작업이 완료된 후에는 `session.endSession()`을 호출하여 세션을 종료합니다.

---

# 샤딩(Sharding) 관련

1. **MongoDB에서 샤딩(Sharding)이란 무엇이며, 이를 통해 데이터베이스 성능을 어떻게 최적화할 수 있는지 설명하세요.**
2. **MongoDB에서 샤드 키(Shard Key)의 역할과, 샤드 키를 선택할 때 고려해야 할 요소들을 설명하세요.**
3. **MongoDB에서 샤딩 구조의 주요 구성 요소(샤드, 쿼리 라우터, 컨피그 서버)를 설명하고, 각 구성 요소가 어떻게 상호작용하는지 서술하세요.**
4. **MongoDB에서 Range-based Sharding과 Hash-based Sharding의 차이점을 설명하고, 각각의 장단점을 비교하세요.**
5. **MongoDB에서 샤딩의 장점과 단점을 설명하고, 샤딩이 적합한 상황과 그렇지 않은 상황에 대해 논하세요.**

---

# 레플리카 세트(Replica Set) 관련

1. **MongoDB에서 레플리카 세트(Replica Set)란 무엇이며, 이 기능을 사용하는 주된 목적에 대해 설명하세요.**
2. **MongoDB 레플리카 세트의 구성 요소인 Primary, Secondary, Arbiter의 역할과 동작 방식을 설명하세요.**
3. **MongoDB에서 레플리카 세트를 사용하는 경우, Primary 서버에 장애가 발생했을 때 어떤 과정으로 장애를 복구하는지 서술하세요.**
4. **MongoDB에서 Secondary 서버를 활용한 읽기 작업 분산이 무엇인지 설명하고, 이 방법이 읽기 성능에 어떤 영향을 미치는지 논하세요.**
5. **레플리카 세트와 샤딩의 차이점을 설명하고, 두 기능을 함께 사용할 경우의 장점에 대해 서술하세요.**