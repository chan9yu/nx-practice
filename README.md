# `Nx`

> 📦 Nx practice repository

<br />

## Nx 란?

현재 가장 많은 기능을 제공하는 모노레포를 위한 도구
<br />
개발자 생산성 향상, CI 성능 최적화, 코드 품질 유지를 위한 최고 수준의 도구라고 소개되어 있다.
<br />

오픈 소스이면서 Nx Cloud라는 유료 상품을 통해 원격 캐싱 및 분산 태스크 수행과 같은 수준 높은 기능을 제공하고 있다.

<br />

## Nx 주요 기능

### `Run Tasks`

nx는 단일 워크스페이스 혹은 전체 워크스페이스들에 대한 태스크 수행 명령어를 가지고 있다.

```shell
# Syntax
nx <target name> <project name> <option overrides>

# Example
nx test products --watch
```

- **nx build <package name>**: 단일 워크스페이스 태스크 실행<br />(해당 워크스페이스에서 build 실행)
- **nx run-many -t build**: 전체 워크스페이스들에 대한 태스크 실행 (build 실행)<br /> (전체 워크스페이스에서 build 실행)
- **nx run-many -t build test**: 전체 워크스페이스들에 대한 여러 태스크 실행<br /> (전체 워크스페이스에서 build와 test 실행)

<br />

### `Cache Task Results`

nx는 캐싱 기능(로컬 캐싱)을 제공하고 있다.

- 태스크 실행 명령어를 실행하면, 여러 방식의 설정 파일로부터 캐싱을 어떻게 하는지 체크한다.
- **nx.json** **project.json** **packages.json** 등을 이용해서 설정한다.

<br />

### `Use Remote Caching`

로컬 캐싱 이외에도 리모트 캐싱 기능을 제공한다.

```shell
# Nx Cloud를 통해 사용이 가능하다.
nx connect-to-nx-cloud
```

<br />

### `Distribution Task Execution`

작업을 분산해서 실행하는 기능을 제공한다.

레포지토리의 핵심이 수정되어 모든 작업을 CI에서 실행해야 하는 경우,
<br />
성능을 개선할 수 있는 유일한 방법은 에이전트 작업을 더 추가하고 작업을 효율적으로 병렬화하는 것뿐이다.

```shell
# 1. Nx Cloud에 연결
nx connect-to-nx-cloud

# 2. CI에서 DTE를 활성화한다.
nx generate @nrwl/workspace:ci-workflow --ci=github
```

<br />

### `Explore the Graph`

모노레포 안에 있는 모든 패키지 간의 의존성 그래프를 시각적으로 보여주는 기능을 제공한다.

```shell
nx graph
```

<br />

### `Automate Updating Dependencies`

사용하는 packages versions들을 업데이트 또는 여러 가지 도구들의 설정을 업데이트하거나 심지어 소스코드도 마이그레이션을 자동으로 수행해 준다.

<br />

### `Enforce Module Boundaries`

모듈의 경계를 강제(?) 하는 기능을 제공한다.

- 코드 분석을 사용하여 프로젝트가 서로의 잘 정의된 공용 API에만 의존할 수 있도록 한다.
- 프로젝트가 서로 의존할 수 있는 방식에 선언적으로 제약을 가할 수 있다.
- Lint 설정을 이용해서 선언적으로 설정한 내용을 바탕으로 제약을 가할 수 있다.

<br />

### `Integrate with Editors`

**Nx Console for VSCode**라는 VSCode 확장 프로그램을 제공하고 있다.

<br />

### `Plugin Features`

공통적으로 사용 가능한 실행기나 코드를 생성해 내는 생성기를 플러그인으로 작성하고 서로 공유할 수 있다.
