# mini-sns-api
👥 회원 (User) & 팔로우 (Follow)

POST /api/users/signup : 회원가입
POST /api/users/login : 로그인
GET /api/users/{userId} : 특정 유저 프로필 보기
POST /api/users/{userId}/follow : 특정 유저 팔로우 하기
DELETE /api/users/{userId}/follow : 팔로우 취소하기


📝 게시글 (Post) & 좋아요 (Like)

POST /api/posts : 게시글 작성
PUT /api/posts/{postId} : 게시글 수정
DELETE /api/posts/{postId} : 게시글 삭제
GET /api/posts : 전체 게시글 목록 조회 (피드)
GET /api/posts/{postId} : 게시글 상세 조회
POST /api/posts/{postId}/likes : 게시글 좋아요 누르기
DELETE /api/posts/{postId}/likes : 게시글 좋아요 취소하기


💬 댓글 (Comment) & 좋아요 (Like)

POST /api/posts/{postId}/comments : 특정 게시글에 댓글 작성
GET /api/posts/{postId}/comments : 특정 게시글의 댓글 목록 조회
POST /api/comments/{commentId}/likes : 댓글 좋아요 누르기
DELETE /api/comments/{commentId}/likes : 댓글 좋아요 취소하기