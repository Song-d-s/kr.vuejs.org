---
title: 테스트
type: guide
order: 402
---

## 소개

신뢰도 높은 애플리케이션을 제작하는데에 있어, 테스트는  새로운 기능을 제작, 코드 리팩토링, 버그 픽스 등등 을 수행하는 개인 혹은 팀에게 중요한 역할을 수행합니다.
비록 테스트에 대한 여러가지 고찰이 있지만, 웹 응용 프로그램에서는 주로 아래 세 가지 범주를 논의합니다.

- 유닛 테스팅
- 컴포넌트 테스팅
- 종단 (End-To-End / E2E) 테스팅

이 섹션에서는 테스트 생태계와 당신의 Vue 애플리케이션 혹은 컴포넌트 라이브러리에 적합한 도구를 고르는 방법에 대한 가이드를 제공하는 것에 중점을 둡니다.

## 유닛 테스팅

### 소개

유닛 테스트는 각 코드 조각을 개별 환경에서 테스트 합니다. 유닛 테스팅의 목적은 개발자로 하여금 그들 자신의 코드에 자신감을 가지도록 하는 것입니다. 의미 있는 테스트를 오롯히 작성함으로써, 새로운 기능이 추가되거나 코드가 리팩토링 되어도 애플리케이션이 기능적이고 안정된 상태를 유지할 수 있다는 확신을 가질 수 있습니다.

Vue 애플리케이션을 유닛 테스팅 하는 것은 다른 유형의 애플리케이션과 크게 다르지 않습니다.

### 프레임워크를 골라봅시다

유닛 테스트에 관한 조언은 프레임워크에 구애받지 않는 경우가 많으므로, 당신의 애플리케이션에 적합한 유닛 테스팅 툴을 평가하는데 필요한 기본적인 가이드라인을 드리겠습니다.

#### 1급 에러 보고 (First-class error reporting)

테스트가 실패한  경우, 유닛 테스팅 프레임워크가 유의미한 에러를 제공하는 것은 상당히 중요합니다. 이는 assertion 라이브러리의 역할입니다. 에러 내용이 자세히 기록된 메시지가 포함된 assertion은 디버깅 시간을 최소화하는데 도와줍니다. assertion 라이브러리는 단순히 어떤 테스트가 실패하였는지 알려주는 것 외에도, 왜 테스트가 실패하였는지에 대한 컨텍스트를 제공합니다 (e.g. 예상되는 결과 vs 실제 수신한 값)

Jest와 같은 유닛 테스팅 프레임워크는 assertion 라이브러리를 포함하고 있습니다. Mocha와 같은 다른 프레임워크는 별도로 assertion 라이브러리를 설치해줘야 합니다. (일반적으로 Chai).

#### 활발한 커뮤니티와 팀

주요 유닛 테스팅 프레임워크는 오픈소스이기 때문에, 활발한 커뮤니티를 가지고 있는 것은 오랜 기간 동안 테스트를 할 수 있는 기능이 지원되고 프로젝트가 적극적으로 유지되도록 보장할 필요가 있는 일부 팀에게 매우 중요할 수 있습니다. 추가로, 활발한 커뮤니티를 갖는 것은 문제가 생길 때마다 더 많은 지원을 받을 수 있다는 장점이 있습니다.

### 프레임워크들

생태계에 많은 도구들이 있지만, 여기 Vue.js 생태계에서 쓰이는 일반적인 유닛 테스팅 도구들을 소개해드립니다.

#### Jest

Jest는 단순함에 초점을 맞춘 Javascript 테스트 프레임워크입니다. Jest는 애플리케이션의 단위 기능들을 테스트하는 대체 수단을 제공하기 위하여 스냅샷을 찍는 유니크한 기능이 있습니다.


**리소스들:**

- [Jest 공식 웹 사이트](https://jestjs.io)
- [공식 Vue 2 CLI 플러그인 - Jest](https://cli.vuejs.org/core-plugins/unit-jest.html)

#### Mocha

Mocha는 유연성에 초점을 맞춘 Javascript 테스트 프레임워크입니다. 이러한 유연성 덕분에 Mocha는 spying이나 (e.g. Sinon) assertion (e.g. Chai)와 같은 일반적인 기능을 다른 라이브러리로부터 가져올 수 있습니다. 또한 Mocha는 Node.js 뿐만 아니라 브라우저에서도 테스트를 실행 할 수 있다는 유니크한 특징을 가지고 있습니다.


**리소스들:**

- [Mocha 공식 웹 사이트](https://mochajs.org)
- [공식 Vue 2 CLI 플러그인 - Mocha](https://cli.vuejs.org/core-plugins/unit-mocha.html)

## 컴포넌트 테스팅

### 소개

많은 Vue 컴포넌트를 테스트 하기 위해서는 DOM 위에(가상 DOM이든 진짜 DOM이든 간에요) 마운트 되어 완전히 작동하고 있는 상태여야 합니다. 이것 역시 프레임워크에 구애받지 않는 컨셉입니다.
결과적으로, 컴포넌트 테스팅 프레임워크들은 유저들에게 테스트를 안정적으로 수행할 뿐만 아니라, Vuex, Vue Router, 그리고 Vue 플러그인들의 통합을 구성하여 Vue에 특화된 편의를 제공하기 위해 만들어졌습니다.

### 프레임워크를 골라봅시다

하단 섹션은 당신의 애플리케이션에 어울리는 컴포넌트 테스팅 프레임워크를 고르기 위해 새겨두어야 할 평가 항목들입니다.

#### Vue 생태계와의 최적의 호환성 제공

가능한 Vue 생태계와 호환성을 가져야 한다는 것이 제 1의 평가 지침이라는 것은 딱히 놀라운 이야기가 아닙니다. 포괄적으로 보일 수 도 있겠지만, 기억해야 할 주요 영역에는 싱글 파일 컴포넌트 (SFC), Vuex, Vue Router 그리고 당신의 애플리케이션과 유관한 다른 Vue 플러그인이 포함됩니다.

#### 1급 에러 보고 (First-class error reporting)

테스트가 실패한  경우, 유닛 테스팅 프레임워크가 유의미한 에러를 제공하는 것은 상당히 중요합니다. 이는 assertion 라이브러리의 역할입니다. 에러 내용이 자세히 기록된 메세지가 포함된 assertion은 디버깅 시간을 최소화하는데 도와줍니다. assertion 라이브러리는 단순히 어떤 테스트가 실패하였는지 알려주는 것 외에도, 왜 테스트가 실패하였는지에 대한 컨텍스트를 제공합니다 (e.g. 예상되는 결과 vs 실제 수신한 값)

### 추천안

#### Vue Testing Library (@testing-library/vue)

Vue Testing Library는 세부 구현 사항에 의존하지 않은 채 컴포넌트를 테스팅 하는데 초점을 둔 도구 모움입니다. 접근성을 염두하고 만들어진 이 라이브러리는, 리팩토링도 봄바람처럼 가볍게 할 수 있도록 만들어 줍니다.

이것의 가이드 원칙은 소프트웨어 사용 방법과 테스트가 유사할 수록, 더 많은 신뢰를 제공할 수 있다는 것입니다.

**리소스들:**

- [공식 Vue Testing Library 웹 사이트](https://testing-library.com/docs/vue-testing-library/intro)

#### Vue Test Utils

Vue Test Utils는 사용자로 하여금 Vue의 특정 API에 대해 접근 할 수 있도록 하는 공식 low-level 컴포넌트 테스팅 라이브러리입니다. 만약 당신이 Vue 애플리케이션이 처음이라면, Vue Test Utils의 추상화인 Vue Testing Library를 사용하는 것을 권해드립니다.


**리소스들:**

- [Vue Test Utils 공식문서](https://vue-test-utils.vuejs.org)
- [Vue Testing Handbook](https://lmiller1990.github.io/vue-testing-handbook/#what-is-this-guide) by Lachlan Miller
- [Cookbook: Unit Testing Vue Components](/v2/cookbook/unit-testing-vue-components.html)

## 종단 (End-To-End / E2E) 테스팅

### 소개

유닛 테스트들이 개발자에게 어느 정도의 자신감을 제공해주었지만, 유닛/컴포넌트 테스트는 배포 환경에 대한 전체 커버리지를 제공하는 데에는 제한적인 능력을 가지고 있습니다. 그 결과 종단 테스트 (E2E)는 애플리케이션의 가장 중요한 측면에 대한 커버리지를 제공합니다 : 유저들이 실제로 애플리케이션을 사용할 때 어떠한 일이 일어나는지 말입니다.

다르게 말하자면, E2E 테스트는 당신의 애플리케이션의 모든 레이어를 검증합니다. 프론트엔드 코드에 국한된 이야기가 아니라, 사용자가 이용할 환경에 있는 벡엔드 서비스와 인프라까지 포함합니다. 유저들의 액션이 당신의 애플리케이션에 미칠 영향을 테스트 함으로서, E2E 테스트는 종종 애플리케이션이 제대로 동작하는지 여부에 대한 신뢰도를 높이는 열쇠가 되는 경우가 잦습니다.

### 프레임워크를 골라봅시다

웹 상에서 시행하는 종단 테스트 (E2E)가 신뢰할 수 없는 (훼손이 쉬운) 테스트와 개발 프로세스 지연으로 악명을 얻은 반면, 최신 E2E 도구는 보다 신뢰할 수 있고 유용한 테스트를 만들기 위해 많은 개선이 이루어졌습니다. 이어지는 섹션에서 애플리케이션에 사용할 테스트 프레임워크를 선택할 때 유의해야할 가이드를 몇 가지 제공합니다.

#### 크로스 브라우저 테스트

종단 (E2E) 테스팅의 주요 장점 중 하나는 애플리케이션을 여러 브라우저 상에서 테스트 할 수 있다는 것입니다. 비록 100% 크로스 브라우저 커버리지가 바람직해보이겠지만, 크로스 브라우저 테스트는 이를 지속적으로 실행하는데에 드는 추가적인 시간과 머신 파워가 팀의 리소스를 절감시킨다는 사실을 기억하길 바랍니다. 결과적으로, 애플리케이션에 있어 어느 정도 레벨의 브라우저 호환성을 유지할 지에 대한 절충안이 필요합니다.


<p class="tip">특정 브라우저에서만 발견되는 문제를 찾기 위한 E2E 개발의 최근 동향은 일반적으로 사용되지 않는 브라우저(e.g., < IE11, 이전 Safari 버전들, etc.)에 대해서는 애플리케이션 모니터링 및 오류 보고 도구 (e.g., Sentry, LogRocket, etc.)를 사용하는 것입니다.</p>

#### 더 빠른 피드백 루프

종단 (E2E) 테스트와 개발의 주요한 문제 중 하나는 전체 내용을 실행하고, 테스트를 하는데 오랜 시간이 걸린다는 것입니다. 전통적으로, 이는 지속적인 통합/개발 (CI/CD) 파이프라인으로만 해결 될 수 있는 문제였습니다. 최신 E2E 테스팅 프레임워크에서는 CI/CD 파이프라인이 이전보다 더 빠르게 실행될 수 있도록 하는 병렬화 기능을 추가함으로서 이 고질적인 문제를 해결하는데 도움을 주었습니다. 추가로, 로컬에서 개발할 때 작업 중인 페이지에 대해 단일 테스트를 선택적으로 실행하는 동시에 테스트에 핫 리로딩을 적용함으로써 개발자의 워크플로우와 생산성을 향상시킬 수 있습니다.

#### 뛰어난 디버깅 경험

개발자들은 일반적으로 터미널 창에 뜬 로그들을 읽음으로서 테스트에서 무엇이 잘못 되었는지 확인하곤 하였지만, 최신 종단(E2E) 테스트 프레임워크는 개발자들이 이미 익숙하게 쓰고 있는 도구들(e.g. 브라우저 개발자 도구)를 활용할 수 있도록 합니다.

#### 헤드리스 모드에서의 가시성

종단 (E2E) 테스트가 지속적인 통합 / 배포 파이프라인에서 수행 될 때, 테스트들은 대게 헤드리스 브라우저에서 구동됩니다 (i.e., 유저들이 볼 수 있는 그래픽 인터페이스가 없는 브라우저). 결과적으로, 에러가 발생하였을 때 최신 E2E 테스트 프레임워크에서 제공하는 주요한 기능은 여러 테스트 스테이지에서 애플리케이션의 스냅샷과 비디오를 보고 오류의 원인을 파악 할 수 있는 기능입니다. 역사적으로, 이러한 통합을 유지하는 것은 지루한 과정들이었습니다.

### 추천안

생태계에 많은 도구들이 있지만, 아래는 Vue.js의 생태계에서 흔히 쓰이는 종단(E2E) 테스트 프레임워크입니다.

#### Cypress.io

Cypress.io 는 최상의 DX과 더불어 애플리케이션을 안정적으로 테스트할 수 있게 함으로써 개발자의 생산성을 향상시키는 것을 목표로 하는 테스트 프레임워크입니다.

**리소스들:**

- [Cypress 공식 웹 사이트](https://www.cypress.io)
- [공식 Vue CLI Cypress 플러그인](https://cli.vuejs.org/core-plugins/e2e-cypress.html)
- [Cypress Testing Library](https://github.com/testing-library/cypress-testing-library)

#### Nightwatch.js

Nightwatch.js는 웹 애플리케이션 뿐만 아니라 Node.js와 통합 테스트 모두에 사용할 수 있는 종단 테스트 프레임워크입니다.

**리소스들:**

- [Nightwatch 공식 웹 사이트](https://nightwatchjs.org)
- [공식 Vue CLI Nightwatch 플러그인](https://cli.vuejs.org/core-plugins/e2e-nightwatch.html)

#### Puppeteer

Puppeteer는 브라우저를 제어하기 위한 높은 수준의 API를 제공하며 다른 테스트 도구들과 (e.g., Jest) 짝을 이루어 애플리케이션을 테스트 할 수 있는 Node.js 라이브러리입니다.

**리소스들:**

- [Puppeteer 공식 웹 사이트](https://pptr.dev)

#### TestCafe

TestCafe는 개발자가 쓰기 쉽고 신뢰할 수 있는 테스트를 만드는데 집중할 수 있도록 쉬운 설정을 제공하는 것을 목표로 하는 Node.js 기반 종단 테스트 프레임워크입니다.

**리소스들:**

- [TestCafe's Official Website](https://devexpress.github.io/testcafe/)
