---
layout: post
title: (JPA-4)MappedSuperclass 공통매핑정보의 재사용
subtitle: feat.Spring
author: Ino
categories: spring
banner:
  image: "https://user-images.githubusercontent.com/95608811/291508517-1966009e-4c10-4089-a793-f3f778f31809.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [java, spring]
sidebar: []
---

## MappedSuperclass: 공통 매핑 정보의 재사용

### 개요

`MappedSuperclass`는 JPA에서 상속 관계 매핑이 아닌 공통 매핑 정보의 재사용을 위해 사용됩니다.   
이 방법은 데이터베이스 설계와 객체지향 설계의 불일치 문제를 해결하는 데 도움을 줍니다.    


### 주요 특징
- 공통 매핑 정보 제공: @MappedSuperclass로 지정된 클래스는 데이터베이스 테이블로 직접 매핑되지 않습니다.
대신, 이 클래스에 정의된 매핑 정보(필드, 관계, 메서드 등)는 상속받는 자식 클래스에게 상속됩니다.    

- 엔티티가 아님: @MappedSuperclass로 지정된 클래스는 엔티티가 아닙니다. 즉, EntityManager를 통해 직접 쿼리하거나 데이터베이스 작업을 할 수 없습니다.

- 상속받는 자식 클래스들의 매핑 정보: 자식 클래스들은 @MappedSuperclass에서 정의된 필드나 메서드를 상속받아 사용할 수 있으며, 각각 독립적인 테이블로 매핑됩니다.

- 재사용성과 유지보수성 향상: 공통적인 매핑 정보를 @MappedSuperclass에 정의함으로써, 코드의 재사용성과 유지보수성이 향상됩니다.

### 사용 예시

```java
@MappedSuperclass
public abstract class BaseEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    // 공통으로 사용되는 필드 및 메서드
    // getters and setters
}

@Entity
public class User extends BaseEntity {
    private String username;
    // 추가적인 필드 및 메서드
    // getters and setters
}

@Entity
public class Product extends BaseEntity {
    private String productName;
    // 추가적인 필드 및 메서드
    // getters and setters
}

```
이 예시에서 BaseEntity 클래스는 @MappedSuperclass로 지정되어 있으며, User와 Product 엔티티가 이를 상속받습니다.     
BaseEntity의 id 필드와 관련 메서드는 User와 Product 엔티티에 모두 상속되며, 각각의 엔티티는 자신만의 테이블로 매핑됩니다.

## 일반적인 JPA에서의 extend : 상속을 쓰는 경우

### Entity 상속
한 엔티티 클래스가 다른 엔티티 클래스를 상속할 때 사용합니다.     
상속받는 클래스는 @Entity 어노테이션으로 표시되며, 데이터베이스 테이블과 매핑됩니다.     
사용되는 상속 전략에는 단일 테이블 상속(SINGLE_TABLE), 조인 테이블 상속(JOINED), 테이블 당 클래스 상속(TABLE_PER_CLASS) 등이 있습니다.

### MappedSuperclass 상속
@MappedSuperclass 어노테이션이 적용된 클래스를 상속받을 때 사용됩니다.    
여러 엔티티 클래스에서 공통으로 사용되는 매핑 정보(필드, 메서드 등)를 정의하는 데 사용됩니다.     
상속받는 엔티티들은 @MappedSuperclass에서 정의된 정보를 재사용할 수 있으며, 각각 독립적인 테이블로 매핑됩니다.

### 결론
MappedSuperclass는 JPA에서 매핑 정보의 중복을 줄이고, 코드의 재사용성 및 유지보수성을 향상시키는 유용한 방법입니다.   
하지만, 이는 엔티티가 아니므로 데이터베이스와의 직접적인 상호작용은 할 수 없습니다.     
따라서, 이를 사용할 때는 엔티티와의 차이점을 명확히 이해하고 적절히 활용해야 합니다.
