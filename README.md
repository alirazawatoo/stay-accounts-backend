# Stay Accounts Backend

A Django REST backend for account roles, rental records, lease documents, regulatory documents, and asynchronous document-analysis workflows.

## Product flow

```text
account + role -> rental / lease records -> document upload
                                      -> background analysis
                                      -> status, response, and chat history
```

The project separates account permissions, lease/rental data, regulation content, Celery tasks, and shared constants. It pairs with [`stay-booking-frontend`](https://github.com/alirazawatoo/stay-booking-frontend).

## Local setup

Configure Django secret settings, PostgreSQL, Redis/Celery, storage, and any document-analysis provider through the local environment, then run:

```bash
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Start the configured worker separately for analysis tasks.

## Boundaries

Uploaded lease and regulation documents can contain sensitive information. Production use requires access-control review, encrypted storage, retention policy, provider data-handling review, audit logging, and deterministic task retry/idempotency.
