---
title: "Utiliser les alertes pour les &#233;v&#233;nements des agents de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualisation des alertes"
  - "Agent de lecture de la file d’attente, alertes"
  - "alertes [réplication SQL Server]"
  - "alertes de réplication prédéfinies [réplication SQL Server]"
  - "Agent de lecture du journal, alertes"
  - "Agent de distribution, alertes"
  - "Agent de fusion, alertes"
  - "agents [réplication SQL Server], alertes"
  - "affichage des alertes"
  - "Agent d’instantané, alertes"
ms.assetid: 8c42e523-7020-471d-8977-a0bd044b9471
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Utiliser les alertes pour les &#233;v&#233;nements des agents de r&#233;plication
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent permettent de surveiller les événements, tels que des événements de l’agent de réplication, à l’aide d’alertes. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent surveille le journal des applications Windows pour les événements qui sont associées aux alertes. Si un tel événement se produit, l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] répond automatiquement, en exécutant une tâche que vous avez définie et/ou en envoyant un e-mail ou un message par radio-messagerie à un opérateur spécifié. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclut un ensemble d’alertes prédéfinies pour les agents de réplication que vous pouvez configurer pour exécuter une tâche et/ou avertir un opérateur. Pour plus d'informations sur la définition d'une tâche à exécuter, consultez la section « Automatisation d'une réponse à une alerte » de la présente rubrique.  
  
 Les alertes suivantes sont installées lorsqu'un ordinateur est configuré en tant que serveur de distribution :  
  
|ID du message|Alerte prédéfinie|Condition provoquant le déclenchement de l'alerte|Entrée d'informations supplémentaires dans msbd..sysreplicationalerts|  
|----------------|----------------------|-----------------------------------------|-----------------------------------------------------------------|  
|14150|**Réplication : succès de l'agent**|Arrêt normal de l'Agent.|Oui|  
|14151|**Réplication : échec de l'agent**|Arrêt de l'Agent en raison d'une erreur.|Oui|  
|14152|**Réplication : nouvelle tentative de l'agent**|L'agent s'arrête après l'échec du renouvellement d'une opération (l'Agent a rencontré une erreur de type serveur non disponible, interblocage, échec de la connexion, ou dépassement du délai d'attente).|Oui|  
|14157|**Réplication : suppression de l'abonnement expiré**|Suppression de l'abonnement expiré|Non|  
|20572|**Réplication : abonnement réinitialisé après l'échec de validation**|Le travail de réponse « Réinitialiser les abonnements après échec de la validation des données » a réussi à réinitialiser un abonnement.|Non|  
|20574|**Réplication : l'Abonné n'a pas réussi la validation des données**|L'Agent de distribution ou de fusion n'a pas réussi la validation des données.|Oui|  
|20575|**Réplication : l'Abonné a passé la validation des données**|L'Agent de distribution ou de fusion a réussi la validation des données.|Oui|  
|20578|**Réplication : arrêt personnalisé de l'Agent**|||  
|22815|**Alerte de détection de conflit d'égal à égal**|L'Agent de distribution a détecté un conflit lorsqu'il essaie d'appliquer une modification à un nœud d'égal à égal.|Oui|  
  
 En plus de ces alertes, le moniteur de réplication comprend un ensemble d'avertissements et d'alertes liées aux états et aux performances. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). Vous pouvez aussi définir des alertes pour d'autres événements de réplication à l'aide de l'infrastructure d'alertes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [créer un événement défini par l’utilisateur](../../../ssms/agent/create-a-user-defined-event.md).  
  
 **Pour configurer des alertes de réplication prédéfinies**  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Configure Predefined Replication Alerts &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md)  
  
## Affichage direct du journal des applications  
 Pour afficher le journal des applications Windows, utilisez le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Observateur d’événements Windows. Le journal des applications comporte les messages d'erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ainsi que des messages se rapportant à toutes les activités de l'ordinateur. À la différence du journal des erreurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], chaque démarrage de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne crée pas un nouveau journal des applications (chaque session [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] écrit des nouveaux événements dans un journal des applications existant) ; en revanche, vous pouvez spécifier la durée de rétention des événements enregistrés. Lorsque vous affichez le journal des applications Windows, vous pouvez filtrer le journal en fonction d'événements spécifiques. Pour plus d'informations, consultez la documentation Windows.  
  
## Automatisation d'une réponse à une alerte  
 La réplication fournit un travail de réponse aux abonnements dont la validation des données échoue ainsi qu'une infrastructure permettant de créer des réponses automatiques supplémentaires aux alertes. Le travail de réponse est intitulé **réinitialisation des abonnements sur Échec de validation des données** et est stocké dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent **travaux** dossier [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations sur l’activation de ce travail de réponse, consultez [configurer des alertes de réplication prédéfinies & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/administration/configure-predefined-replication-alerts-sql-server-management-studio.md). Si certains articles d'une publication transactionnelle ne peuvent pas être validés, le travail de réponse ne réinitialise que ces articles. Si certains articles d'une publication de fusion ne peuvent pas être validés, le travail de réponse réinitialise tous les articles de la publication.  
  
### Infrastructure d'automatisation des réponses  
 Généralement, lorsqu'une alerte survient, la seule information dont vous disposez pour vous aider à comprendre la raison de l'alerte et l'action appropriée à entreprendre, se trouve dans le message d'alerte lui-même. L'analyse de ces informations peut être fastidieuse et sujette à erreurs. La réplication facilite l’automatisation des réponses en fournissant des informations supplémentaires sur l’alerte dans la **sysreplicationalerts** (table système), les informations fournies sont déjà analysées dans une forme facilement utilisée par des programmes personnalisés.  
  
 Par exemple, si les données dans le **Sales.SalesOrderHeader** table chez l’abonné A fait échouer la validation, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut déclencher le message 20574, vous informant de l’échec. Le message reçu est : « Abonné 'A', l’abonnement à l’article 'SalesOrderHeader' de la publication 'MyPublication' échec de validation des données ».  
  
 Si vous créez une réponse basée sur le message, vous devez extraire manuellement du message, le nom de l'Abonné, le nom de l'article, le nom de la publication et l'erreur. Toutefois, étant donné que l’Agent de Distribution et l’Agent de fusion écrivent ces mêmes informations pour **sysreplicationalerts** (ainsi que des détails tels que le type d’agent, l’heure de l’alerte, la base de données de publication, la base de données de l’abonné et le type de publication), le travail de réponse peut interroger directement les informations pertinentes à partir de la table. Bien que la ligne exacte ne peut pas être associée à une instance spécifique de l’alerte, la table a un **état** colonne, ce qui peut être utilisé pour effectuer le suivi des entrées. Les entrées de cette table sont conservées pendant la période de rétention de l'historique.  
  
 Par exemple, si vous voulez créer un travail dans [!INCLUDE[tsql](../../../includes/tsql-md.md)], en réponse au message d'alerte 20574, vous pouvez utiliser la logique suivante :  
  
```  
declare @publisher sysname, @publisher_db sysname, @publication sysname, @publication_type int, @article sysname, @subscriber sysname, @subscriber_db sysname, @alert_id int  
declare hc cursor local for select publisher, publisher_db, publication, publication_type, article, subscriber,   
  subscriber_db, alert_id from   
  msdb..sysreplicationalerts where  
  alert_error_code = 20574 and status = 0  
  for read only  
open hc  
fetch hc into  @publisher, @publisher_db, @publication, @publication_type, @article, @subscriber, @subscriber_db, @alert_id  
while (@@fetch_status <> -1)  
begin  
/* Do custom work  */  
/* Update status to 1, which means the alert has been serviced. This prevents subsequent runs of this job from doing this again */  
update msdb..sysreplicationalerts set status = 1 where alert_id = @alert_id  
 fetch hc into  @publisher, @publisher_db, @publication, @publication_type, @article, @subscriber, @subscriber_db, @alert_id  
end  
close hc  
deallocate hc  
```  
  
## Voir aussi  
 [Administration de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Méthodes conseillées pour l'administration de la réplication](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Analyse & #40 ; Réplication & #41 ;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  