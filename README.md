

## 📁 Estrutura do Projeto

```
src/
 └── main/
      ├── java/
      │    └── com/speakai/
      │          ├── application/          # Camada de Aplicação
      │          │     ├── dto/            # Data Transfer Objects
      │          │     │     ├── auth/
      │          │     │     │     ├── LoginRequest.java
      │          │     │     │     ├── LoginResponse.java
      │          │     │     │     ├── RegisterRequest.java
      │          │     │     │     └── RefreshTokenRequest.java
      │          │     │     │
      │          │     │     ├── deck/
      │          │     │     │     ├── CreateDeckRequest.java
      │          │     │     │     ├── UpdateDeckRequest.java
      │          │     │     │     └── DeckResponse.java
      │          │     │     │
      │          │     │     ├── flashcard/
      │          │     │     │     ├── CreateFlashcardRequest.java
      │          │     │     │     ├── UpdateFlashcardRequest.java
      │          │     │     │     └── FlashcardResponse.java
      │          │     │     │
      │          │     │     ├── study/
      │          │     │     │     ├── StartStudySessionRequest.java
      │          │     │     │     ├── ReviewFlashcardRequest.java
      │          │     │     │     └── StudySessionResponse.java
      │          │     │     │
      │          │     │     └── ai/
      │          │     │           ├── GenerateExampleRequest.java
      │          │     │           └── GenerateAudioRequest.java
      │          │     │
      │          │     ├── mapper/         # Mappers para conversão
      │          │     │     ├── UserMapper.java
      │          │     │     ├── DeckMapper.java
      │          │     │     └── FlashcardMapper.java
      │          │     │
      │          │     ├── port/           # Ports (interfaces para serviços externos)
      │          │     │     ├── ai/
      │          │     │     │     ├── ExampleGeneratorPort.java
      │          │     │     │     └── AudioGeneratorPort.java
      │          │     │     │
      │          │     │     └── notification/
      │          │     │           └── EmailServicePort.java
      │          │     │
      │          │     └── usecases/       # Casos de Uso
      │          │           ├── auth/
      │          │           │     ├── LoginUseCase.java
      │          │           │     ├── RegisterUserUseCase.java
      │          │           │     ├── RefreshTokenUseCase.java
      │          │           │     └── GoogleLoginUseCase.java
      │          │           │
      │          │           ├── deck/
      │          │           │     ├── CreateDeckUseCase.java
      │          │           │     ├── RenameDeckUseCase.java
      │          │           │     ├── UpdateDeckUseCase.java
      │          │           │     └── DeleteDeckUseCase.java
      │          │           │
      │          │           ├── flashcard/
      │          │           │     ├── CreateFlashcardUseCase.java
      │          │           │     ├── UpdateFlashcardUseCase.java
      │          │           │     └── DeleteFlashcardUseCase.java
      │          │           │
      │          │           ├── study/
      │          │           │     ├── StartStudySessionUseCase.java
      │          │           │     ├── ReviewFlashcardUseCase.java
      │          │           │     └── GetNextFlashcardUseCase.java
      │          │           │
      │          │           └── ai/
      │          │                 ├── GenerateExamplesUseCase.java
      │          │                 └── GenerateAudioUseCase.java
      │          │
      │          ├── domain/               # Camada de Domínio
      │          │     ├── entity/         # Entidades de Domínio
      │          │     │     ├── User.java
      │          │     │     ├── Deck.java
      │          │     │     ├── Flashcard.java
      │          │     │     └── StudyReview.java
      │          │     │
      │          │     ├── valueobject/    # Value Objects
      │          │     │     ├── Email.java
      │          │     │     ├── Password.java
      │          │     │     └── StudyInterval.java
      │          │     │
      │          │     ├── repository/     # Interfaces de Repositório
      │          │     │     ├── UserRepository.java
      │          │     │     ├── DeckRepository.java
      │          │     │     ├── FlashcardRepository.java
      │          │     │     └── StudyReviewRepository.java
      │          │     │
      │          │     ├── service/        # Domain Services
      │          │     │     ├── StudyDomainService.java
      │          │     │     └── RepetitionScheduler.java  // Algoritmo SM-2
      │          │     │
      │          │     ├── event/          # Domain Events
      │          │     │     ├── UserRegisteredEvent.java
      │          │     │     ├── DeckCreatedEvent.java
      │          │     │     ├── FlashcardReviewedEvent.java
      │          │     │     └── StudySessionCompletedEvent.java
      │          │     │
      │          │     └── exception/      # Exceções de Domínio
      │          │           ├── InvalidEmailException.java
      │          │           ├── DeckNotFoundException.java
      │          │           └── FlashcardNotFoundException.java
      │          │
      │          ├── infrastructure/       # Camada de Infraestrutura
      │          │     ├── controller/    # Controllers REST
      │          │     │     ├── AuthController.java
      │          │     │     ├── DeckController.java
      │          │     │     ├── FlashcardController.java
      │          │     │     ├── StudyController.java
      │          │     │     └── AiController.java
      │          │     │
      │          │     ├── persistence/   # Persistência
      │          │     │     ├── jpa/
      │          │     │     │     ├── entity/        # Entidades JPA
      │          │     │     │     │     ├── UserEntity.java
      │          │     │     │     │     ├── DeckEntity.java
      │          │     │     │     │     ├── FlashcardEntity.java
      │          │     │     │     │     └── StudyReviewEntity.java
      │          │     │     │     │
      │          │     │     │     ├── repository/    # Repositórios JPA
      │          │     │     │     │     ├── JpaUserRepository.java
      │          │     │     │     │     ├── JpaDeckRepository.java
      │          │     │     │     │     ├── JpaFlashcardRepository.java
      │          │     │     │     │     └── JpaStudyReviewRepository.java
      │          │     │     │     │
      │          │     │     │     └── adapter/       # Adapters (implementações)
      │          │     │     │           ├── UserRepositoryAdapter.java
      │          │     │     │           ├── DeckRepositoryAdapter.java
      │          │     │     │           ├── FlashcardRepositoryAdapter.java
      │          │     │     │           └── StudyReviewRepositoryAdapter.java
      │          │     │     │
      │          │     │     └── mapper/   # Mappers JPA <-> Domain
      │          │     │           ├── UserEntityMapper.java
      │          │     │           ├── DeckEntityMapper.java
      │          │     │           └── FlashcardEntityMapper.java
      │          │     │
      │          │     ├── security/       # Segurança
      │          │     │     ├── jwt/
      │          │     │     │     ├── JwtTokenProvider.java
      │          │     │     │     ├── JwtAuthenticationFilter.java
      │          │     │     │     └── JwtAuthenticationEntryPoint.java
      │          │     │     │
      │          │     │     └── userdetails/
      │          │     │           ├── CustomUserDetails.java
      │          │     │           └── CustomUserDetailsService.java
      │          │     │
      │          │     ├── ai/            # Integrações com IA
      │          │     │     ├── OpenAiExampleGenerator.java
      │          │     │     └── OpenAiAudioGenerator.java  // TTS
      │          │     │
      │          │     ├── config/        # Configurações
      │          │     │     ├── SecurityConfig.java
      │          │     │     ├── CorsConfig.java
      │          │     │     ├── OpenAiConfig.java
      │          │     │     ├── JpaConfig.java
      │          │     │     └── EventConfig.java
      │          │     │
      │          │     └── exception/     # Exception Handlers
      │          │           ├── GlobalExceptionHandler.java
      │          │           ├── ResourceNotFoundException.java
      │          │           └── UnauthorizedException.java
      │          │
      │          └── SpeakAiApplication.java
      │
      └── resources/
            ├── application.yml
            ├── application-dev.yml
            ├── application-prod.yml
            └── db/migration/              # Flyway Migrations
                 ├── V1__create_users_table.sql
                 ├── V2__create_decks_table.sql
                 ├── V3__create_flashcards_table.sql
                 ├── V4__create_study_reviews_table.sql
                 └── V5__create_indexes.sql
```