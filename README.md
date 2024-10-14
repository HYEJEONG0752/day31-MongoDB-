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
    - **수평적 확장성 :** 데이터베이스가 증가하는 데이터 양과 트래픽을 처리하기 위해 여러 서버에 걸쳐 데이터를 분산할 수 있는 능력을 의미합니다.
        수평적 확장성은 시스템의 성능을 향상시키고, 더 많은 사용자를 지원할 수 있도록 해줍니다. 
        이는 수직적 확장성(서버의 성능을 높이는 것)과는 달리, 여러 대의 서버를 추가하여 시스템의 용량을 늘리는 방식입니다.
    - **샤딩이 수평적 확장을 지원하는 방식 :** <br>
        - 데이터 분산 : 데이터를 여러 샤드에 분산하여 저장합니다.<br>
        - 샤딩 키 : 데이터를 어떻게 분산할지를 결정하는 기준이 되는 필드로, 키를 기반으로 MongoDB는 데이터를 특정샤드에 할당합니다.<br>
        - 쿼리 라우팅 : 클라이언트의 요청은 쿼리라우터를 통해 적절한 샤드로 전달됩니다.<br>
        - 부하 분산 : 샤딩을 통해 데이터와 요청이 여러 서버에 분산되므로, 특정 샤드에 트래픽이 집중되지 않습니다.<br>
        - 확장성 : 데이터베이스의 용량이나 성능이 부족할 경우, 새로운 서버를 추가하고 기존 데이터의 일부를 새로운 샤드로 재분배함으로써 시스템을 확장할 수 있습니다.<br>
        - 고가용성 및 내결함성 : 샤딩은 데이터의 복제본을 여러 샤드에 저장할 수 있는 기능과 결합되어, 데이터의 가용성을 높입니다.<br>
        만약 하나의 샤드가 실패하더라도 다른 샤드에서 데이터를 계속 사용할 수 있습니다.<br>
        - 성능 최적화 : 각 샤드는 독립적으로 쿼리를 처리할 수 있기 때문에, 데이터베이스의 성능이 향상됩니다.

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
    (1) MongoClient 및 세션 생성: `MongoClient`를 사용하여 MongoDB에 연결하고, 트랜잭션을 처리할 세션을 생성합니다.</br>
    (2) 트랜잭션 시작: `session.startTransaction()` 메서드를 통해 트랜잭션을 시작합니다.</br>
    (3) 업데이트 작업 수행:</br>
        - 첫 번째 `updateOne()`에서는 송금자의 계좌에서 100달러를 차감하고, 두 번째 `updateOne()`에서는 수신자의 계좌에 100달러를 추가합니다.</br>
        - 두 작업 모두 동일한 트랜잭션 세션 내에서 처리되므로, 둘 중 하나라도 실패하면 전체 트랜잭션이 롤백됩니다.</br>
    (4) 트랜잭션 커밋: 모든 작업이 성공적으로 완료되면 `session.commitTransaction()`을 호출하여 트랜잭션을 커밋합니다.</br>
    (5) 트랜잭션 롤백: 만약 작업 중 오류가 발생하면, `session.abortTransaction()`을 호출하여 트랜잭션을 취소하고 롤백합니다.</br>
    (6) 세션 종료: 작업이 완료된 후에는 `session.endSession()`을 호출하여 세션을 종료합니다.

---

# 샤딩(Sharding) 관련

1. **MongoDB에서 샤딩(Sharding)이란 무엇이며, 이를 통해 데이터베이스 성능을 어떻게 최적화할 수 있는지 설명하세요.**
    - **샤딩이란?**
        샤딩은 대규모 데이터베이스에서 데이터를 수평적으로 분할하여 여러 서버에 분산 저장하는 방법입니다.
    - **성능 최적화 방법**
        - 수평적 확장성 : 데이터가 여러 샤드에 분산되어 저장되므로, 데이터베이스의 용량과 처리 능력을 쉽게 확장할 수 있습니다.<br>
        - 부하 분산 : 쿼리와 데이터 저장 작업이 여러 샤드에 분산되어 처리되므로, 단일 서버에 대한 부하가 줄어들고 응답 시간이 개선됩니다.<br>
        - 병렬 처리 : 여러 샤드에서 동시에 쿼리를 처리할 수 있어, 전체적인 처리 속도가 향상됩니다.

2. **MongoDB에서 샤드 키(Shard Key)의 역할과, 샤드 키를 선택할 때 고려해야 할 요소들을 설명하세요.**
    - 샤드 키는 데이터를 샤드에 분산 저장하는 기준이 되는 필드입니다. 샤드 키는 각 도큐먼트를 특정 샤드에 매핑하는데 사용됩니다.
    - 선택 시 고려해야 할 요소
        - 균형 잡힌 데이터 분포 : 샤드 키는 데이터를 균등하게 분산시켜야 하며, 특정 샤드에 데이터가 집중되지 않도록 해야합니다.
        - 쿼리 패턴 : 자주 사용되는 쿼리에서 샤드 키가 포함되어야 하며, 이를 통해 쿼리 성능을 최적화할 수 있습니다.
        - 변경 가능성 : 샤드 키는 변경이 어려운 필드여야 하며, 변경 시 데이터 이동이 발생할 수 있으므로 신중하게 선택해야 합니다.
        - 읽기/쓰기 비율 : 읽기와 쓰기 작업의 비율을 고려하여 샤드 키를 선택해야 하며, 특정 작업에 대한 성능 저하를 방지해야 합니다.

3. **MongoDB에서 샤딩 구조의 주요 구성 요소(샤드, 쿼리 라우터, 컨피그 서버)를 설명하고, 각 구성 요소가 어떻게 상호작용하는지 서술하세요.**
    - **샤드** : 데이터의 실제 저장소로, 갹 샤드는 데이터의 일부를 저장합니다. 샤드는 독립적인 MongoDB 인스턴스일 수 있ㅇ며, 데이터의 수평적 분할을 담당합니다.
    - **쿼리라우터** : 클라이언트의 요청을 적절한 샤드로 라우팅하는 역할을 합니다. 
    MongoDB에서는 `mongos` 프로세스가 쿼리 라우터 역할을 하며, 클라이언트의 쿼리를 수집하고, 필요한 샤드에 요청을 전달합니다.
    - **컨피그 서버** : 샤딩 클러스터의 메타데이터를 저장하는 서버입니다. 
    샤드의 위치, 샤드 키 정보, 데이터 분포 등을 관리하며, 클러스터의 상태를 유지하는 데 필수적입니다.

    - **상호작용**:
        - 클라이언트가 쿼리를 보내면, 쿼리 라우터가 컨피그 서버에서 메타데이터를 조회하여 적절한 샤드를 결정합니다.
        - 쿼리 라우터는 해당 샤드에 쿼리를 전달하고, 샤드는 요청된 데이터를 처리하여 결과를 반환합니다.
        - 결과는 쿼리 라우터를 통해 클라이언트에게 전달됩니다.

4. **MongoDB에서 Range-based Sharding과 Hash-based Sharding의 차이점을 설명하고, 각각의 장단점을 비교하세요.**
    - **`Range-based Sharding`** :
        - 데이터를 특정 범위에 따라 샤드에 분산합니다.
        - 장점 : 특정 범위의 데이터를 쉽게 조회할 수 있어, 범위 쿼리에 유리합니다.
        - 단점 : 데이터가 불균형하게 분포될 수 있으며, 특정 샤드에 부하가 집중될 수 있습니다.

    - **`Hash-based Sharding`** :
        - 샤드 키의 해시 값을 기반으로 데이터를 분산합니다. 해시 함수를 사용하여 데이터를 샤드에 고르게 분산시킵니다.
        - 장점 : 데이터가 균등하게 분포되어 부하가 고르게 분산됩니다.
        - 단점 :  범위 쿼리에 대한 성능이 저하될 수 있으며, 특정 범위의 데이터를 조회하기 위해 모든 샤드를 검색해야 할 수 있습니다.

5. **MongoDB에서 샤딩의 장점과 단점을 설명하고, 샤딩이 적합한 상황과 그렇지 않은 상황에 대해 논하세요.**
    - **장점**: 데이터베이스의 용량과 성능을 수평적으로 확장(확장성)할 수 있고, 
    여러 샤드에 쿼리와 데이터 저장 작업을 분산(부하 분산)시켜 성능을 향상시킬수 있으며,
    샤드를 여러 서버에 분산하여 장애 발생시에도 데이터 접근이 가능(고가용성)합니다.
    - **단점**: 샤딩 구조가 복잡해져 관리와 유지보수가 어려워질 수 있고(복잡성),
    특정 쿼리 패턴에 따라 성능이 저하되어 모든 샤드를 검색해야하는 경우가 발생할 수 있으며(쿼리 성능 저하),
    샤드 키 변경 시 데이터 이동이 필요하여, 이 과정에서 성능 저하가 발생할 수 있습니다.
    - **적합한 상황**: 대규모 데이터베이스에서 데이터의 수평적 확장이 필요한 경우, 읽기/쓰기의 높은 성능이 요구되는 애플리케이션.
    - **적합하지 않은 상황**: 데이터 양이 적거나 단일 서버에서 처리할 수 있는 경우, 데이터베이스 관리의 복잡성을 줄이고자 하는 경우.

---

# 레플리카 세트(Replica Set) 관련

1. **MongoDB에서 레플리카 세트(Replica Set)란 무엇이며, 이 기능을 사용하는 주된 목적에 대해 설명하세요.**
    - **레플리카 세트**:
    MongoDB의 고가용성 및 데이터 복구를 위한 기능으로, 하나의 Primary노드와 여러 개의 Secondary노드로 구성됩니다.
    레플리카 세트는 데이터의 복제본을 유지하여 데이터 손실을 방지하고, 시스템의 가용성을 높이는 데 사용됩니다.
    - **주된 목적**:
        - 고가용성 : Primary서버에 장애가 발생하더라도 Secondary 서버가 자동으로 Primary로 승격되어 서비스 중단을 최소화합니다.
        - 데이터 복구 : 데이터가 여러 서버에 복제되어 저장되므로, 데이터 손실 시 복구가 용이합니다.
        - 읽기 성능 향상 : Secondary 서버에서 읽기 작업을 수행할 수 있어, 읽기 부하를 분산할 수 있습니다.

2. **MongoDB 레플리카 세트의 구성 요소인 Primary, Secondary, Arbiter의 역할과 동작 방식을 설명하세요.**
    - **Primary** : 모든 쓰기 작업을 처리하는 노드입니다. Primary는 클라이언트의 요청을 받아 데이터를 기록하고, 이를 Secondary 서버에 복제합니다.
    Primary서버에 장애가 발생하면, 레플리카 세트 내의 다른 노드 중 하나가 자동으로 Primary로 승격됩니다.
    - **Secondary** : Primary서버의 데이터를 복제하여 저장하는 노드입니다. Secondary는 주로 읽기 작업을 처리하며 Primary에서 발생한 변경 사항을 지속적으로 동기화합니다.
    Secondary 서버는 Primary의 데이터를 읽을 수 있지만, 쓰기 작업은 수행할 수 없습니다.
    - **Arbiter** : 데이터의 저장소를 가지지 않는 노드로, 주로 투표를 통해 Primary 선출 과정에 참여합니다. 
    Arbiter는 데이터 복제를 하지 않지만, 레플리카 세트의 홀수 개수를 유지하여 장애 조치시 안정성을 높입니다.
    Arbiter는 리소스가 적은 환경에서 사용되먀, 데이터 저장소가 필요 없는 경우에 유용합니다.

3. **MongoDB에서 레플리카 세트를 사용하는 경우, Primary 서버에 장애가 발생했을 때 어떤 과정으로 장애를 복구하는지 서술하세요.**<br>
    **(1) 장애감지 :** Primary서버에 장애가 발생하면, Secondary 서버들은 일정 시간 동안 Primary와의 연결이 끊어진 것을 감지합니다.<br>
    **(2) 선출과정 :** 장애가 감지되면, 레플리카 세트 내의 Secondary 서버들이 새로운 Primary를 선출하기 위한 투표를 시작합니다.<br>
    이 과정에서 Arbiter가 참여할 수 있습니다.<br>
    **(3) Primary 승격 :** 투표를 통해 가장 많은 표를 받은 Secondary 서버가 새로운 Primary로 승격됩니다.<br>
    이 과정은 자동으로 이루어지며, 클라이언트는 새로운 Primary에 연결하여 계속해서 작업을 수행할 수 있습니다.<br>
    **(4) 데이터 동기화 :** 새로운 Primary가 선출된 후, 나머지 Secondary 서버들은 새로운 Primary의 데이터를 동기화하여 일관성을 유지합니다.<br>

4. **MongoDB에서 Secondary 서버를 활용한 읽기 작업 분산이 무엇인지 설명하고, 이 방법이 읽기 성능에 어떤 영향을 미치는지 논하세요.**
    - Secondary 서버에서 읽기 요청을 처리하여 Primary 서버의 부하를 줄이는 방법입니다. 
    MongoDB에서는 읽기 우선 순위를 설정하여 클라이언트가 Secondary 서버에서 데이터를 읽도록 할 수 있습니다.
    - **읽기 성능에 미치는 영향 :**
        - 부하 분산 : Primary서버의 부하가 줄어들어, 전체 시스템의 성능이 향상됩니다. 특히 읽기 작업이 많은 애플리케이션에서 효과적입니다.
        - 응답 시간 개선 : Secondary 서버가 Primary 서버와 가까운 위치에 있을 경우, 읽기 응답 시간이 단축될 수 있습니다.
        - 일관성 문제 : Secondary 서버는 Primary의 데이터를 비동기적으로 복제하므로, 최신 데이터가 반영되지 않을 수 있습니다.

5. **레플리카 세트와 샤딩의 차이점을 설명하고, 두 기능을 함께 사용할 경우의 장점에 대해 서술하세요.**
    - **차이점 :**
        - 레플리카 세트 : 데이터의 복제본을 유지하여 고가용성과 데이터 복구를 목적으로 합니다.
        모든 데이터가 여러 노드에 복제되어 있으며, 주로 읽기 성능 향상과 장애 조치를 위해 사용됩니다.
        - 샤딩 : 데이터를 수평적으로 분할하려 여러 서버에 분산 저장하는 방법입니다. 
        대규모 데이터베이스에서 성능을 최적화하고 확장성을 제공하기 위해 사용됩니다.
    - **함께 사용 시 장점 :**
        - 고가용성과 확장성 : 샤딩을 통해 데이터베이스의 용량과 성능을 수평적으로 확장하면서, 레플리카 세트를 통해 각 샤드의 고가용성을 유지할 수 있습ㄴ디ㅏ.
        - 부하 분산 : 읽기 작업을 Secondary서버에서 처리하면서, 샤딩을 통해 데이터의 부하를 분산시킬 수 있습니다.
        - 장애 복구 : 샤딩된 환경에서도 레플리카 세트를 사용하여 각 샤드의 데이터 복구 및 장애 조치를 자동으로 수행할 수 있습니다.