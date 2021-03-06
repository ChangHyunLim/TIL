### MySQL 쿼리에서 1=1 이 있을 경우와 없을 경우의 성능 차이
---
쿼리에서 `1=1` 있을떄와 없을때 쿼리가 차이가 나는 경우를 발견 했다.  
```SQL
select	COUNT(DISTINCT(P.id)) AS count
FROM 	P P
inner join C C on P.id = C.p_id
WHERE	P.s NOT IN ( 'A', 'D', '0', '1', '2', '9', 'O', 'P', 'Q', 'R') AND
        C.c_s IN ('5', '6', '7', '9');
        
        
SELECT    COUNT(DISTINCT(P.id)) AS count 
FROM      P P 
INNER JOIN C C ON P.id = C.p_id 
WHERE     '1 = 1' AND
        P.s NOT IN ( 'A', 'D', '0', '1', '2', '9', 'O', 'P', 'Q', 'R') AND  
        C.c_s IN ( '5', '6', '7', '9')
```
`1=1` 있을때와 없을때 둘다 처음 조회할때는 시간차이가 크지 않는데. 같은 쿼리를 다시 조회할 경우 `1=1`이 없으면 상당히 빠르게 동작 한다.(10ms 이내.) 하지만 `1=1`이 있는 쿼리 같은 경우 처음 조회할때와 거의 같은 시간이 소요 된다. 내 생각에는 캐싱된 쿼리를 수행하느냐 수행 못하느냐의 차이로 보이는데 확실치 않아서 팀장님께 질문 드렸다. 

팀장님은 여쭤보니 다음과 같은 답변을 주셨다. 
>`1=1`이 있는 경우에는 query optimizer에 영향을 줄 것으로 생각되는데 우선 쿼리 캐싱의 경우 쿼리가 완료된 최후의 조건을 기준으로 생성하기 때문에, 해당 조건은 삭제될 것으로 보입니다. field연관성이 없기 때문에 1=1은 삭제한 조건으로 캐싱이 될 것이고, 다음 순간의 쿼리에서 1=1이 들어온 경우에는 저 값들이 동적인 조건이기 때문에 캐싱된 데이터를 바로 불러오지 못할 것으로 보입니다. 1=1, 1=2, 10=10 등등 다양한 경우의 수가 존재하기 때문에요

**출처**
- 회사 슬랙(!?)