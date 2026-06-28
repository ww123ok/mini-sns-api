# mini-sns-api

### 👥 회원 (User) & 팔로우 (Follow)
* `POST /api/users/signup` : 회원가입
* `POST /api/users/login` : 로그인
* `GET /api/users/{userId}` : 특정 유저 프로필 보기
* `POST /api/users/{userId}/follow` : 특정 유저 팔로우 하기
* `DELETE /api/users/{userId}/follow` : 팔로우 취소하기

### 📝 게시글 (Post) & 좋아요 (Like)
* `POST /api/posts` : 게시글 작성
* `PUT /api/posts/{postId}` : 게시글 수정
* `DELETE /api/posts/{postId}` : 게시글 삭제
* `GET /api/posts` : 전체 게시글 목록 조회 (피드)
* `GET /api/posts/{postId}` : 게시글 상세 조회
* `POST /api/posts/{postId}/likes` : 게시글 좋아요 누르기
* `DELETE /api/posts/{postId}/likes` : 게시글 좋아요 취소하기

### 💬 댓글 (Comment) & 좋아요 (Like)
* `POST /api/posts/{postId}/comments` : 특정 게시글에 댓글 작성
* `GET /api/posts/{postId}/comments` : 특정 게시글의 댓글 목록 조회
* `POST /api/comments/{commentId}/likes` : 댓글 좋아요 누르기
* `DELETE /api/comments/{commentId}/likes` : 댓글 좋아요 취소하기


## 🗄 데이터베이스 설계 (ERD 구조)

### 1. users (회원)
* `id` (PK) : 회원 고유 번호
* `email` : 이메일 (로그인 ID)
* `password` : 비밀번호
* `nickname` : 닉네임
* `created_at` : 가입일시

### 2. follows (팔로우 매핑 테이블)
* `id` (PK) : 팔로우 고유 번호
* `follower_id` (FK -> users.id) : 팔로우를 누른 회원
* `following_id` (FK -> users.id) : 팔로우를 당한 회원

### 3. posts (게시글)
* `id` (PK) : 게시글 고유 번호
* `user_id` (FK -> users.id) : 작성자 고유 번호
* `content` : 게시글 본문
* `created_at` : 작성일시

### 4. post_likes (게시글 좋아요 매핑 테이블)
* `id` (PK) : 게시글 좋아요 고유 번호
* `user_id` (FK -> users.id) : 좋아요를 누른 회원
* `post_id` (FK -> posts.id) : 좋아요를 받은 게시글

### 5. comments (댓글)
* `id` (PK) : 댓글 고유 번호
* `post_id` (FK -> posts.id) : 대상 게시글 고유 번호
* `user_id` (FK -> users.id) : 댓글 작성자 고유 번호
* `content` : 댓글 내용
* `created_at` : 작성일시

### 6. comment_likes (댓글 좋아요 매핑 테이블)
* `id` (PK) : 댓글 좋아요 고유 번호
* `user_id` (FK -> users.id) : 좋아요를 누른 회원
* `comment_id` (FK -> comments.id) : 좋아요를 받은 댓글