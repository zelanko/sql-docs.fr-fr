---
title: Concepts des exécutables de l’agent de réplication | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e533edec149513e240efb938d5fb9aad634e7cf8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047709"
---
# <a name="replication-agent-executables-concepts"></a>Concepts des exécutables de l'agent de réplication
  Il est possible de contrôler par programme les agents de réplication de différentes manières :  
  
-   en utilisant les interfaces de programmation d'agent managé dans l'espace de noms <xref:Microsoft.SqlServer.Replication> ;  
  
-   En appelant les fichiers exécutables de l'agent à partir de l'invite de commandes avec des paramètres définis.  
  
 Lorsque les agents de réplication sont directement appelés à partir de l'invite de commandes, il est possible d'accéder par programme aux agents à partir de scripts dans des fichiers de commandes. Lorsqu'un agent est appelé à partir de l'invite de commandes, il s'exécute sous le compte de sécurité [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows de l'utilisateur qui a appelé l'agent ou qui a lancé le fichier de commandes.  
  
 Il est possible d'exécuter des instances des agents de réplication suivants à l'aide de fichiers exécutables.  
  
-   [Replication Distribution Agent](../agents/replication-distribution-agent.md)  
  
-   [Agent de lecture du journal des réplications](../agents/replication-log-reader-agent.md)  
  
-   [Replication Merge Agent](../agents/replication-merge-agent.md)  
  
-   [Agent de lecture de la file d’attente de réplication](../agents/replication-queue-reader-agent.md)  
  
-   [Replication Snapshot Agent](../agents/replication-snapshot-agent.md)  
  
 Lorsque vous appelez des agents de réplication, vous pouvez utiliser des profils de performances pour transmettre automatiquement un jeu défini de paramètres au fichier exécutable de l'agent. Pour plus d'informations, voir [Replication Agent Profiles](../agents/replication-agent-profiles.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants décrivent comment appeler les agents de réplication à partir de l'invite de commandes. Il est également possible d'appeler les agents de réplication au moyen de Replication Management Objects. Pour plus d’informations, consultez [Synchroniser des abonnements &#40;réplication&#41;](../synchronize-data.md).  
  
> [!NOTE]  
>  Les sauts de ligne figurant dans ces exemples ont été ajoutés afin d'améliorer la lisibilité. Dans un fichier de commandes, les commandes doivent figurer sur une seule ligne.  
  
### <a name="running-the-snapshot-agent"></a>Exécution de l'Agent d'instantané  
 Cet exemple de fichier de commandes appelle l’Agent d’instantané à partir de l’invite de commandes afin de générer un instantané pour la publication **AdvWorksSalesOrdersMerge**.  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a>Exécution de l'Agent de distribution  
 Cet exemple de fichier de commandes appelle l’Agent de distribution à partir de l’invite de commandes afin de répliquer en continu les modifications de la publication **AdvWorksProductTran** sur un abonné pour un abonnement par émission de données.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a>Exécution de l'Agent de fusion  
 Cet exemple de fichier de commandes appelle l’Agent de fusion à partir de l’invite de commandes afin de synchroniser un abonnement par extraction de données avec la publication **AdvWorksSalesOrdersMerge**.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
