# 📄 Informe Técnico del Taller

## Nombre del Taller
Taller 5 - Evaluación de Seguridad con STRIDE

## Integrantes del equipo
- Mateo González  
- Santiago Sánchez

## Descripción general del trabajo
El objetivo del taller fue identificar riesgos de seguridad en procesos y componentes críticos mediante el marco STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).  

El análisis se aplicó a Macondo Magic Softwares y otros escenarios relacionados, documentados en el archivo adjunto `tablas-stride-macondo.pdf`. En este se revisaron procesos como la gestión de documentación e informes mensuales, la recepción de requerimientos, la integración de pruebas funcionales, las pruebas de interoperabilidad, la validación de seguridad y cumplimiento, la UAT (User Acceptance Testing), el despliegue controlado, el monitoreo post-entrega y la gestión de tareas en Macondo.  

Cada tabla STRIDE permitió identificar amenazas, vulnerabilidades y estrategias de mitigación, fortaleciendo la visión de seguridad del ciclo de vida de los proyectos.

## Proceso de desarrollo
1. Selección de escenarios críticos: se eligieron procesos representativos del ciclo de vida de desarrollo (desde la recepción de requerimientos hasta el monitoreo post-producción).  
2. Aplicación de STRIDE: se construyeron tablas que documentan amenazas en cada categoría STRIDE, con sus vulnerabilidades, impactos potenciales y estrategias de mitigación (anexo `tablas-stride-macondo.pdf`).  
3. Consolidación del análisis: se redactó este informe para describir los hallazgos, supuestos y controles propuestos.  

La metodología se basó en priorizar procesos con mayor exposición a riesgos de seguridad y continuidad operativa.

## Análisis del modelo propuesto
El modelo resultante se estructura en múltiples tablas STRIDE (una por proceso crítico), que permiten un enfoque modular de la seguridad.  

- Envío de informes: se identificó como el proceso más central. Los principales riesgos son la suplantación de identidad, manipulación de datos, falta de trazabilidad y divulgación no autorizada. Se propuso implementar autenticación fuerte (2FA), control de versiones, registros de auditoría y permisos basados en roles.  
- Recepción de requerimientos y mockups: los riesgos más relevantes fueron la suplantación en la entrega de artefactos y la alteración de mockups durante el tránsito. Se propusieron medidas como autenticación de remitentes y repositorios versionados.  
- Integración y pruebas funcionales: se identificaron amenazas relacionadas con dispositivos falsos y manipulación de scripts de prueba. Se recomendaron prácticas como autenticación mutua de dispositivos, checksums y entornos aislados.  
- Pruebas de interoperabilidad: los riesgos principales incluyeron manipulación de mensajes, spoofing de servicios y DoS por sobrecarga de módulos. Las mitigaciones incluyen autenticación mTLS, firmado de mensajes y circuit breakers.  
- Seguridad y cumplimiento: se resaltó el robo de tokens, manipulación de reportes y fuga de datos biomédicos. Se propuso uso de tokens de corta vida, firmado digital y cifrado con servicios certificados.  
- Pruebas de Usuario (UAT): se detectaron riesgos por uso de datos reales, manipulación de builds y repudio de testers. Mitigaciones: uso de datos sintéticos, builds firmadas y registros auditables de aprobación.  
- Entrega y despliegue controlado: amenazas como despliegues no autorizados o exposición de secretos en pipelines. Se recomendaron MFA en CI/CD, firmado de artefactos y secret management.  
- Monitoreo post-entrega: los riesgos incluyeron falsificación de métricas y manipulación de logs. Estrategias: firmas digitales en telemetría, logs inmutables y RBAC estricto en dashboards.  
- Gestión de tareas en Macondo: el mayor riesgo identificado fue la dependencia de procesos manuales y credenciales débiles en GitHub. Mitigaciones: digitalización de acuerdos, MFA y control estricto de permisos.  

Este enfoque integral refuerza la seguridad desde la generación y envío de documentación hasta la operación continua del sistema, priorizando el proceso de envío de informes por su impacto contractual y de reputación.

## Diagrama final entregado
Nota: las tablas detalladas de STRIDE se encuentran en el documento adjunto `tablas-stride-macondo.pdf`.

## Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Cliente/PO | Actor | Define y aprueba requerimientos | Cliente |
| Scrum Master | Actor | Facilita la daily, toma notas y gestiona tareas | Equipo |
| Equipo de desarrollo | Actor | Desarrolla, prueba y mantiene los sistemas | Equipo |
| GitHub | Componente | Repositorio y tablero de gestión de tareas | Cliente |
| Correo electrónico corporativo | Componente | Medio principal de envío de informes mensuales | Equipo |
| Google Drive compartido | Componente | Almacenamiento de informes y documentos | Equipo |
| Sistemas externos | Componente | Plataformas de pago, servicios SaaS y APIs externas | Proveedor |
| SLA | Entidad | Compromisos de servicio a cumplir | Cliente–Proveedor |

## Investigación complementaria

Tema investigado:  
Buenas prácticas de seguridad aplicadas al marco STRIDE y al ciclo de vida de proyectos (SDLC).

Resumen:  
STRIDE clasifica amenazas en seis categorías: suplantación, alteración, repudio, divulgación de información, denegación de servicio y escalamiento de privilegios. Aplicarlo en diferentes etapas del ciclo de vida permite prevenir riesgos específicos según el contexto.  

Entre las buenas prácticas derivadas se incluyen:  
- Autenticación y cifrado en la gestión de requerimientos e intercambio de información.  
- Control de integridad y trazabilidad en informes, pruebas y despliegues.  
- Principio de menor privilegio y MFA en accesos a sistemas y repositorios.  
- Planes de continuidad ante fallos o ataques de denegación de servicio.  
- Anonimización de datos sensibles en entornos de validación y pruebas.  

Estas medidas están alineadas con marcos como OWASP, NIST y normativas como GDPR o HIPAA.  

En el caso de Macondo, el análisis STRIDE evidenció que la gestión y envío de informes es el punto más crítico y requiere controles de autenticación, trazabilidad, integridad y confidencialidad más robustos.

## Referencias
- [1] Microsoft. The STRIDE Threat Model. https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats  
- [2] OWASP. Threat Modeling. https://owasp.org/www-community/Threat_Modeling  
- [3] GitHub Docs. Best practices for organizations, teams, and repositories. https://docs.github.com/  
- [4] Documento de trabajo: Stride.pdf (entregado como parte del taller).  

Este documento hace parte de la entrega del Taller 5 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana.
