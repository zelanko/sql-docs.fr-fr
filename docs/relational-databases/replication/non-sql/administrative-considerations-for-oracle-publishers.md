---
title: "Consid&#233;rations sur l&#39;administration des serveurs de publication Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publication Oracle [réplication SQL Server], considérations administratives"
  - "administration de la réplication, publication Oracle"
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Consid&#233;rations sur l&#39;administration des serveurs de publication Oracle
  Quand un serveur de publication Oracle est configuré et que les mécanismes de suivi des modifications de la réplication sont en place, les administrateurs du système de base de données Oracle peuvent continuer à utiliser les utilitaires de base de données standard d'Oracle et à effectuer des tâches courantes d'administration du système. Cependant, il faut être attentif aux effets que peuvent avoir certaines tâches d'administration sur les données publiées.  
  
 À l'exception de la suppression ou de la modification d'une colonne qui est publiée pour réplication, ou de la suppression ou de la modification de n'importe quel objet de réplication, ces considérations ne s'appliquent pas aux publications d'instantané.  
  
## Importation et chargement de données  
 Les déclencheurs sont utilisés dans le suivi des modifications pour les publications transactionnelles sur Oracle. Les modifications apportées aux tables publiées peuvent être répliquées vers les Abonnés seulement si les déclencheurs de réplication s'exécutent quand une mise à jour, une insertion ou une suppression se produit. Les utilitaires Oracle Import et SQL*Loader d'Oracle ont tous deux des options qui affectent l'activation des déclencheurs quand des lignes sont insérées dans des tables répliquées avec ces utilitaires.  
  
### Oracle Import  
 Avec Oracle Import, vous pouvez définir l’option **Ignorer** à 'y' ou ' ne (la valeur par défaut est n '). Si **Ignorer** est définie sur n », la table est supprimée et recréée lors de l’importation. Cela supprime les déclencheurs de réplication et désactive la réplication. Si **Ignorer** est définie à 'y', importation va tenter de charger les lignes dans la table existante, ce qui déclenche les déclencheurs de réplication. Par conséquent, vérifiez **Ignorer** est définie à 'y' lors de l’importation dans une table répliquée avec l’outil d’importation.  
  
### SQL*Loader  
 Avec SQL\*Loader, vous pouvez définir l’option **direct** sur « true » ou « false » (la valeur par défaut est « false »). Si **direct** est définie sur « false », les lignes sont insérées à l’aide des instructions INSERT conventionnelles, qui activent les déclencheurs de réplication. Si **direct** est définie sur « true », la charge est optimisée et les déclencheurs ne sont pas activés. Par conséquent, vérifiez **direct** a la valeur 'false' lors du chargement dans une table répliquée avec SQL * outil de chargeur.  
  
## Modifications d'objets publiés  
 Les actions suivantes ne requièrent pas de considérations particulières :  
  
-   Reconstruction d'index sur des tables publiées.  
  
-   Ajout de déclencheurs de l'utilisateur à une table publiée.  
  
 L'action suivante nécessite l'arrêt de toutes les activités sur les tables publiées :  
  
-   Déplacement d'une table publiée.  
  
 Les actions suivantes nécessitent la suppression de la publication, la réalisation de l'opération, puis la recréation de la publication :  
  
-   Troncation d'une table publiée.  
  
-   Renommage d'une table publiée.  
  
-   Ajout d'une colonne à une table publiée.  
  
-   Ajout ou modification d'une colonne qui est publiée pour réplication.  
  
-   Réalisation d'opérations sans journalisation.  
  
## Suppression ou modification d'objets de réplication  
 Vous devez supprimer et reconfigurer le serveur de publication si vous supprimez ou si vous modifiez des tables, des déclencheurs, des séquences ou des procédures stockées de suivi au niveau d'un serveur de publication. Pour obtenir une liste partielle de ces objets, consultez la page [les objets créés sur le serveur de publication Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md).  
  
 Pour plus d’informations sur la suppression et la reconfiguration du serveur de publication, consultez la section « Modifications sont effectuées et nécessitent la reconfiguration du serveur de publication » dans la rubrique [Dépannage des serveurs de publication Oracle](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).  
  
## Voir aussi  
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Problèmes et limitations de conception des serveurs de publication Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)   
 [Présentation de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  