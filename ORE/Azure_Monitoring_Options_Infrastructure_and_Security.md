**AZURE MONITORING OPTIONS**

Infrastructure, Network, Security and Governance Monitoring

  -----------------------------------------------------------------------
  **Recommended operating model: use Azure Monitor and Log Analytics as
  the observability foundation; Microsoft Defender for Cloud for posture
  and workload protection; Microsoft Sentinel for centralized SIEM/SOAR;
  and Azure Policy plus Diagnostic Settings to enforce consistent
  telemetry collection.**
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

# How to use this document

- Use the tables as a service-selection checklist during landing zone,
  workload onboarding, ARB, SOC and operational-readiness reviews.

- An option may serve more than one monitoring domain. Selection should
  be based on workload criticality, data sensitivity, incident-response
  requirements, retention policy and cost.

- For regulated workloads, define ownership, alert severity, response
  targets, log retention, access control and test evidence for every
  enabled monitoring control.

# Recommended layered model

  -----------------------------------------------------------------------
  **Layer**                    **Recommended capabilities**
  ---------------------------- ------------------------------------------
  **1. Collection**            Diagnostic Settings, Azure Monitor Agent,
                               Data Collection Rules, platform metrics
                               and activity logs

  **2. Observability data      Azure Monitor Metrics, Log Analytics,
  platform**                   Application Insights, Managed Prometheus

  **3. Visualization and       Workbooks, Managed Grafana, alerts,
  detection**                  Defender analytics and Sentinel analytics

  **4. Response**              Action Groups, automation runbooks, Logic
                               Apps playbooks and ITSM workflows

  **5. Governance**            Azure Policy, Resource Graph, secure
                               access, retention, archive and cost
                               controls
  -----------------------------------------------------------------------

# 1. Core infrastructure and application monitoring

  ------------------------------------------------------------------------------
  **Monitoring    **Primary scope** **Key capabilities**    **Best-fit use**
  option**                                                  
  --------------- ----------------- ----------------------- --------------------
  Azure Monitor   Azure-wide        Central collection,     Foundation for
                  observability     analysis,               infrastructure and
                  platform          visualization, alerts,  application
                                    autoscale and           observability
                                    integrations            

  Azure Monitor   Near-real-time    Fast charting, metric   Operational health,
  Metrics         numeric telemetry alerts, dynamic         capacity and
                                    thresholds and          performance signals
                                    multi-resource analysis 

  Azure Monitor   Central log data  KQL queries,            Troubleshooting,
  Logs / Log      platform          cross-resource          forensics, reporting
  Analytics                         analysis, workbooks,    and long-term
                                    alerts, retention and   analysis
                                    export                  

  Azure Activity  Subscription      Administrative audit    Governance and
  Log             control plane     trail, export through   monitoring changes
                                    diagnostic settings and to Azure resources
                                    alerting                

  Diagnostic      Per-resource log  Routes telemetry to Log Standardized
  Settings        and metric        Analytics, Event Hubs   centralized
                  routing           or Storage              collection and SIEM
                                                            forwarding

  Azure Monitor   Guest OS          Centralized collection  VM and Azure
  Agent and Data  telemetry         rules, filtering,       Arc-enabled server
  Collection      collection        transformation and      monitoring
  Rules                             destination control     

  VM Insights     Azure and hybrid  Curated VM views,       Server fleet health,
                  virtual machines  health and dependency   performance and
                                    visualization           dependency
                                                            troubleshooting

  Container       AKS and           Curated cluster views,  Kubernetes platform
  Insights        Kubernetes        health analysis,        operations
                                    Prometheus integration  
                                    and alerts              

  Managed Service Cloud-native      Managed collection,     Kubernetes and
  for Prometheus  metrics           PromQL and integration  open-source metrics
                                    with Azure Managed      monitoring
                                    Grafana                 

  Azure Managed   Visualization     Managed Grafana         Cross-platform
  Grafana                           dashboards, role        operations
                                    integration and shared  dashboards
                                    visualization           

  Application     Application       Distributed tracing,    Web apps, APIs,
  Insights        performance       application map,        Functions and
                  monitoring        transaction search,     distributed
                                    failures and            applications
                                    performance views       

  OpenTelemetry   Vendor-neutral    Standardized            Modern cloud-native
  with Azure      application       instrumentation and     and multi-platform
  Monitor         instrumentation   Azure Monitor export    application
                                                            observability

  Azure Monitor   Interactive       Reusable operational    NOC, SOC and
  Workbooks       reporting         and security reports    service-owner
                                    with drill-down views   dashboards

  Azure Monitor   Event detection   Notifications,          Proactive incident
  Alerts and      and notification  automation triggers,    detection and
  Action Groups                     ITSM/webhook            response routing
                                    integration and alert   
                                    processing              

  Azure Service   Azure service     Personalized health     Cloud provider
  Health          conditions        views and alerts        outage and
                                                            maintenance
                                                            awareness

  Azure Resource  Individual Azure  Resource-specific       Distinguishing
  Health          resources         health diagnosis and    platform issues from
                                    alerts                  workload issues

  Azure Resource  At-scale resource Fast cross-subscription Finding monitoring
  Graph           inventory         queries and inventory   gaps and
                                    views                   configuration drift
  ------------------------------------------------------------------------------

**2.Network and connectivity monitoring**

  ------------------------------------------------------------------------------
  **Monitoring   **Primary        **Key capabilities**    **Best-fit use**
  option**       scope**                                  
  -------------- ---------------- ----------------------- ----------------------
  Network        Azure network    Connection              Network
  Watcher        diagnostics      troubleshoot, IP flow   troubleshooting and
                                  verify, next hop,       validation
                                  packet capture and      
                                  topology                

  Connection     End-to-end       Continuous tests and    Hybrid connectivity
  Monitor        connectivity     alerts for Azure,       and application-path
                                  on-premises and         monitoring
                                  external endpoints      

  NSG Flow Logs  Network traffic  Traffic visibility,     Network security
  / Virtual      metadata         flow analytics and SIEM analysis,
  Network Flow                    integration             troubleshooting and
  Logs                                                    baselining

  Traffic        Network flow     Visual traffic          Network behavior and
  Analytics      analytics        patterns, hotspots and  communication analysis
                                  security-oriented       
                                  insights                

  ExpressRoute   Private hybrid   Circuit dashboards,     Monitoring
  monitoring     connectivity     alerts and Connection   on-premises-to-Azure
                                  Monitor tests           private connectivity

  VPN Gateway    Site-to-site and Gateway diagnostics,    Hybrid VPN
  monitoring     point-to-site    logs, metrics and       availability and
                 VPN              alerts                  performance

  Azure Load     Load-balanced    Dependency/topology     Layer 4 service
  Balancer       services         views and health        availability
  insights                        analysis                

  Application    Layer 7 delivery Backend health,         Web application
  Gateway and    and web security latency, HTTP status    delivery and
  WAF monitoring                  and WAF event analysis  protection

  Azure Front    Global           Global endpoint         Internet-facing global
  Door           application      visibility, analytics   applications
  monitoring     delivery         and alerts              

  Azure Firewall Network security Workbooks, metrics,     Central egress/ingress
  monitoring     control          policy analytics and    and segmentation
                                  SIEM integration        monitoring

  DDoS           DDoS-protected   Attack alerts,          Public endpoint DDoS
  Protection     public IP        mitigation visibility   monitoring
  telemetry      resources        and post-attack         
                                  reporting               
  ------------------------------------------------------------------------------

# 3. Security, identity and compliance monitoring

  -------------------------------------------------------------------------------
  **Monitoring   **Primary scope**   **Key capabilities**    **Best-fit use**
  option**                                                   
  -------------- ------------------- ----------------------- --------------------
  Microsoft      Cloud security      Secure Score,           Cloud security
  Defender for   posture and         regulatory compliance,  posture management
  Cloud          workload protection CSPM and Defender plans and threat
                                     for supported workloads protection

  Defender CSPM  Multicloud posture  Risk prioritization,    Prioritizing and
                 management          posture recommendations remediating cloud
                                     and security governance risks

  Defender for   Azure, hybrid and   Workload threat         Windows/Linux server
  Servers        multicloud servers  detection, Defender for protection
                                     Endpoint integration    
                                     and vulnerability       
                                     management              

  Defender for   AKS and supported   Posture, registry       Container supply
  Containers     container           scanning and runtime    chain and runtime
                 environments        threat detection        security

  Defender for   Azure Storage       Threat detection and    Protecting blobs,
  Storage        accounts            malware scanning        files and storage
                                     options                 data paths

  Defender for   Azure and supported Vulnerability           Database posture and
  SQL /          database services   assessment and advanced threat monitoring
  Databases                          threat protection       

  Defender for   Azure Key Vault     Threat alerts linked to Protecting secrets,
  Key Vault                          identity and resource   certificates and
                                     context                 keys

  Defender for   Azure control plane Detection of anomalous  Control-plane threat
  Resource                           or malicious management detection
  Manager                            activity                

  Defender for   API posture and     API security posture    Protecting published
  APIs           runtime signals for and threat detection    APIs
                 supported APIs                              

  Microsoft      Cloud-native SIEM   Analytics rules,        Central SOC
  Sentinel       and SOAR            incidents, hunting,     detection,
                                     UEBA, threat            investigation and
                                     intelligence, workbooks automated response
                                     and playbooks           

  Microsoft      Cross-domain        Incident correlation,   Unified
  Defender XDR   detection and       advanced hunting and    investigation across
                 response            coordinated response    Microsoft security
                                                             domains

  Microsoft      Identity monitoring Log Analytics/Sentinel  Authentication,
  Entra ID logs                      integration, workbooks  directory and
                                     and alerting            application identity
                                                             monitoring

  Microsoft      Identity risk       Risk investigation and  Identity threat
  Entra ID       detection           Conditional             monitoring
  Protection                         Access-based            
                                     remediation             

  Privileged     Privileged access   Alerts, audit history   Monitoring
  Identity                           and privileged-role     just-in-time
  Management                         oversight               administrative
  monitoring                                                 access

  Azure Policy   Configuration       Deny, audit, modify and Enforcing required
  compliance     governance          deploy-if-not-exists    diagnostics and
                                     controls plus           security baselines
                                     compliance reporting    

  Regulatory     Control-framework   Compliance views and    Security governance
  Compliance     posture             evidence-oriented       and audit readiness
  dashboard                          tracking                

  Microsoft      Microsoft data and  Audit search,           Data governance and
  Purview Audit  compliance activity compliance              compliance
  / data                             investigation and SIEM  monitoring
  governance                         export where supported  
  integrations                                               
  -------------------------------------------------------------------------------

# 4. Integration, automation, retention and cost options

  --------------------------------------------------------------------------
  **Monitoring   **Primary      **Key capabilities**    **Best-fit use**
  option**       scope**                                
  -------------- -------------- ----------------------- --------------------
  Automation     Automated      Execute runbooks,       Repeatable
  runbooks /     remediation    playbooks, ticket       operations and SOC
  Logic Apps                    creation, enrichment    response
                                and containment actions 

  Event Hubs     Telemetry      High-throughput         Enterprise
                 streaming      streaming to external   integration and
                                SIEM or analytics       dual-routing
                                platforms               patterns

  Storage        Low-cost log   Longer-term immutable   Retention, audit and
  Accounts for   archive        or lifecycle-managed    forensic archive
  archive                       storage patterns        

  Azure Monitor  Continuous     Continuous export to    Downstream
  data export    export from    Event Hubs or Storage   analytics, archive
                 Log Analytics                          and integration

  ITSM /         Incident       Creates or updates      Operational
  ticketing      workflow       operational/security    accountability and
  integration                   work items through      SLA tracking
                                supported connectors or 
                                workflows               

  Azure Cost     Monitoring     Budgets, analysis,      Controlling
  Management for cost           exports and cost alerts observability and
  monitoring     governance                             security monitoring
  spend                                                 cost
  --------------------------------------------------------------------------

# Enterprise implementation checklist

- Create an approved telemetry architecture that defines central versus
  workload-specific Log Analytics workspaces and Sentinel boundaries.

- Use Azure Policy to audit or deploy required Diagnostic Settings and
  monitoring agents where technically supported.

- Forward subscription Activity Logs and priority resource logs to
  approved monitoring and security destinations.

- Define a minimum logging profile by resource type, including required
  categories, metrics, retention and archive.

- Enable Defender for Cloud plans based on workload risk, not as a
  blanket assumption; document licensing and coverage decisions.

- Integrate high-value security sources with Microsoft Sentinel and
  define analytics rules, incident ownership and playbooks.

- Create alert standards covering severity, naming, thresholds,
  suppression, action groups, escalation and testing.

- Monitor hybrid dependencies such as ExpressRoute, DNS, firewalls,
  private endpoints, identity and certificate expiration.

- Implement RBAC and privileged-access controls for workspaces,
  Sentinel, Defender and automation assets.

- Control ingestion cost through filtering, Data Collection Rules, table
  plans, retention tiers, commitment tiers and periodic usage review.

- Test dashboards, alerts, case creation and response procedures before
  production approval; retain evidence for ARB and audit reviews.
