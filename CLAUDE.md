# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

LogWatch Admin - Next.js 16 (App Router) 기반 실시간 로그 모니터링 웹 어드민 시스템

**기술 스택:**
- Next.js 16 (App Router)
- TypeScript
- Tailwind CSS v4

## 개발 명령어

```bash
# 의존성 설치
npm install

# 개발 서버 시작 (localhost:3010)
npm run dev

# 프로덕션 빌드
npm run build

# 프로덕션 서버 시작
npm run start

# 린트 검사
npm run lint
```

## 아키텍처 구조

### 라우팅 구조 (Next.js App Router)

- **(dashboard)** 라우트 그룹: 루트 경로 `/`에서 Sidebar + Header 레이아웃 사용
  - `/` - 대시보드 메인
  - `/logs` - 로그 목록 및 검색
  - `/alerts` - 알림 관리
  - `/settings` - 시스템 설정

- **(auth)** 라우트 그룹: 중앙 정렬 레이아웃 (Sidebar 없음)
  - `/login` - 로그인
  - `/register` - 회원가입

- **api** 디렉토리: API 라우트 핸들러
  - `/api/logs` - 로그 조회
  - `/api/alerts` - 알림 규칙 관리
  - `/api/stats` - 대시보드 통계
  - `/api/auth/*` - 인증

### 컴포넌트 구조

- **ui/**: 재사용 가능한 UI 프리미티브 (Button, Input, Card 등)
- **layout/**: 셸 컴포넌트 (Sidebar, Header)
- **features/**: 기능별 복합 컴포넌트 (로그 테이블, 알림 설정 등)

### 서비스 레이어

- **services/**: API 클라이언트 함수 및 외부 서비스 연동
- **lib/**: 공유 유틸리티, 상수, 헬퍼 함수
- **hooks/**: 커스텀 React 훅
- **types/**: TypeScript 타입 정의

## 코딩 컨벤션

### Import 별칭
`@/*`는 `src/*`에 매핑됨
```typescript
import { Sidebar } from "@/components/layout/Sidebar";
```

### 컴포넌트 Export
Named export 사용 (default export 사용 금지)
```typescript
export function LogTable() { ... }
```

### API 응답
`NextResponse.json()`으로 반환
```typescript
import { NextResponse } from "next/server";
export async function GET() {
  return NextResponse.json({ logs: [] });
}
```

## 주요 기능 요구사항

### 대시보드
- 실시간 로그 스트림 모니터링
- 로그 레벨별 필터링 (ERROR, WARN, INFO, DEBUG)
- 시간대별 로그 발생 추이 차트
- 핵심 지표 요약 카드

### 로그 검색 및 분석
- 키워드 기반 로그 검색
- 날짜/시간 범위 필터
- 로그 소스별 분류
- 상세 로그 뷰어

### 알림 관리
- 임계값 기반 알림 규칙 설정
- 알림 이력 조회
- 알림 채널 관리 (이메일, 슬랙 등)

### 시스템 관리
- 사용자 계정 관리
- 로그 수집 소스 설정
- 보존 정책 관리
