# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI를 활용한 시스템 아키텍처 설계의 자동화와 효율화를 학습하고 실습하기 위한 공간이다.

## Repository Structure

- Root repo: `Claude-MCP-Proj/`
- This subproject lives at: `mcp/architectureLab/`
- Root `.gitignore` excludes `.DS_Store` files

## Persona

사용자는 시스템 엔지니어이자 디자이너다. 정밀하고 신뢰성 있는 제어를 최우선으로 한다.

## Engineering Principles

- 모든 세부 사항을 나열하지 않는다. 핵심 구성 요소와 그들 간의 관계에 집중한다.
- 컴포넌트를 연결하는 화살표를 통해 데이터 흐름과 제어 흐름을 명확히 표시한다.

## Design Principles

- 다이어그램은 Mermaid 문법을 사용한다.
- 불필요한 장식을 배제한 미니멀한 브랜드 무드를 유지한다.
- 각 모듈의 명칭은 의도가 정확한 표현만 사용한다.

## Mermaid Activation Rules

### 문법 혼용 금지

자동 방식(`->>+`, `-->>-`)과 수동 방식(`activate`, `deactivate`)을 절대 혼용하지 않는다.

- **수동 방식 (기본)**: `->>` 와 `activate` / `deactivate` 만 사용한다.
- **자동 방식**: `->>+` 와 `-->>-` 만 사용한다.

### 제어 블록 내부 activate/deactivate 금지

- participant는 제어 블록(`alt`/`else`/`loop`/`opt`) 진입 전에 `activate` 한다.
- 모든 제어 블록이 종료된 후에 `deactivate` 한다.
- 제어 블록 내부에서 `activate`/`deactivate`를 절대 사용하지 않는다.
- `activate`와 `deactivate`는 반드시 1:1로 대응시킨다.

### 금지 패턴

- 분기 안에서 `deactivate` 후 `loop` 안에서 다시 `activate`
- 분기마다 개별 `deactivate`
- 제어 블록 내부에서 participant 생명주기를 시작하거나 종료

## Learning Goal

최종 목표는 draw.io 연동 또는 MCP를 통해 아키텍처 설계 과정을 자동화하는 시스템을 구축하는 것이다.
