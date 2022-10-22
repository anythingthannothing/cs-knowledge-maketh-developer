# MVC Pattern

## < 목표 >
### 1. MVC 패턴이 무엇인지 설명할 수 있다.
### 2. MVC 패턴을 구성하는 요소들에 대해 설명할 수 있다.

---

MVC 패턴은 데이터를 담당하는 Model, UI를 담당하는 View, 비즈니스 로직을 담당하는 Controller   
세 가지 구성요소를 통해 소프트웨어를 설계하는 디자인 패턴이다.(본 문서에서는 웹으로 통칭)   
웹의 발전 단계 초기에는 간단한 HTML부터 시작하여 코드의 복잡성이 낮았으나,   
CSS, JavaScript의 등장으로 어플리케이션이 점점 더 복잡해지면서   
유지 보수의 편의성과 원활한 협업을 위해 등장하였다.   
소프트웨어의 디자인 패턴 중 가장 널리 알려진 디자인 패턴이며,   
MVVM(모델-뷰-뷰모델), MVP(모델-뷰-프리젠터), MVW(모델-뷰-왓에버) 등 다른 많은 디자인 패턴에 영향을 끼쳤다.   
말 그대로 'M**' 계열 디자인 패턴의 근본인 셈이라고 할 수 있다.

---

## 1. MVC 패턴을 왜 사용할까?
MVC 패턴의 가장 큰 목적은 '관심사의 분리'다.   
RESTful한 API를 위해 클라이언트와 서버를 분리하듯,   
MVC 패턴 또한 UI, 데이터, 비즈니스 로직을 각각 분리하여   
더 효율적인 협업과 생산성 향상을 가능하게 한다.   

---

## 2. MVC 패턴의 세 가지 구성요소
### ❗ 프레임워크와 프로젝트별로 MVC를 구성하는 방식은 다를 수 있습니다.
> MVC 패턴
>> ![MVC 패턴의 세 가지 구성요소](/assets/mvc/mvc-pattern.png)   
>> 출처: Google Developer
### 1. Controller
Controller는 MVC 패턴의 핵심 요소로,
웹 어플리케이션의 제어 로직, 비즈니스 로직 등을 담당한다.
제어 로직과 비즈니스 로직은 쉽게 풀어 설명할 것도 없이   
UI와 데이터 제어 이외의 모든 로직을 컨트롤러가 담당한다고 할 수 있다.   
View에 필요한 데이터를 Model에 요청하여 뷰에 다시 전달하거나,   
데이터의 변경이 필요할 경우 Model에 요청하는 역할도 Controller가 한다.
View와 Model 사이의 중개자라고 할 수 있다.
> Controller 코드 예시
```javascript
module.exports.showPost = async (req, res) => {
  // request의 param으로부터 post의 id를 추출하여
  // view 렌더링에 필요한 데이터를 Model로부터 전달받는 코드
  const { id } = req.params;
  const categories = await Category.find({}).populate("subcategories");
  const post = await Post.findById(id).populate({
    path: "comments",
    populate: {
      path: "author",
    },
  });
  if (!post) { // Model로부터 데이터를 전달받지 못한 경우
    req.flash("error", "포스트를 찾을 수 없습니다 :(");
    return res.redirect("/posts");
  }
  // Model로부터 전달받은 데이터를 동적 템플릿 엔진에 전달한다.
  res.render("posts/show", { categories, post });
};
```

### 2. Model
Model은 데이터를 담당하는 부분으로 데이터를 저장, 수정하거나   
Controller의 요청에 대해 데이터를 조회하여 전달하는 역할을 한다.   
데이터와 관련된 모든 로직을 Model이 담당한다고 할 수 있으며,   
ORM, ODM이 등장하며 데이터의 Schema를 정의하는 역할도 Model이 맡게 되었다.
> Model 코드 예시
```javascript
// 추후 업데이트
```

### 3. View
View는 사용자에게 보여지는 화면으로 기능적인 코드와는 분리된 부분이다.   
말 그대로 앱이 데이터를 보여주는 방식을 정의하는 코드로   
표시할 데이터를 컨트롤러로부터 전달받아 렌더링에 활용한다.   
> View 코드 예시
```pug
if success && success.length
    div(role='alert').alert.alert-success.alert-dismissible.fade.show
        em #{success}
        button(type="button" data-bs-dismiss="alert" aria-label="Close").btn-close
if error && error.length
    div(role="alert").alert.alert-danger.alert-dismissible.fade.show
        em #{error}
        button(type="button" data-bs-dismiss="alert" aria-label="Close").btn-close
```

---

## Summary
MVC는 Model - View - Controller의 약자로, 소프트웨어 개발을 위한 디자인 패턴이다.   
웹앱의 복잡성이 증가함에 따라 '관심사의 분리'를 위해 등장하였다.   
Controller는 UI, 데이터를 제외한 모든 로직을 처리하며,   
Model은 소프트웨어의 데이터와 관련된 모든 로직을,   
View는 사용자에게 보여줄 인터페이스를 담당한다.   
웹 어플리케이션의 복잡도가 점점 더 높아지며 MVC을 기반으로 한 다양한 패턴이 등장하였으며,   
프레임워크마다 MVC 패턴을 정의하고 구현하는 방식에는 차이가 존재한다.

---

> 추천 자료
>> [Article] MDN Web Docs: https://developer.mozilla.org/en-US/docs/Glossary/MVC   
>> [Youtube] Web Dev Simplified: https://www.youtube.com/watch?v=DUg2SWWK18I

> 추가로 공부하면 좋을 주제들
>> 가고 싶은 기업의 채용 공고에 기재되어 있는 디자인 패턴,,,
