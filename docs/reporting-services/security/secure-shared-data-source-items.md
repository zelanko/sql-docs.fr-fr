---
title: "S&#233;curiser les &#233;l&#233;ments de source de donn&#233;es partag&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sources de données partagées [Reporting Services]"
  - "sources de données [Reporting Services], partagées"
  - "sécurité [Reporting Services], sources de données"
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# S&#233;curiser les &#233;l&#233;ments de source de donn&#233;es partag&#233;e
  Vous pouvez définir la sécurité sur un élément de source de données partagée afin d'en activer ou d'en désactiver l'accès.  
  
 Un utilisateur qui dispose d’un accès minimal à une source de données partagée (par exemple, l’accès accordé par le rôle **Explorateur**) peut visualiser la liste des rapports qui utilisent l’élément, à condition qu’il soit autorisé à afficher les rapports eux-mêmes.  
  
 Un utilisateur qui dispose d’un accès supplémentaire (tel que celui conféré par le rôle **Gestionnaire de contenu**) peut consulter et définir les propriétés de la source de données partagée.  
  
 Pour définir la sécurité, vous créez une attribution de rôle qui spécifie quel compte d'utilisateur ou de groupe dispose de l'accès à la source de données partagée. Les utilisateurs qui ont accès à un élément de source de données partagée peuvent changer son nom, sa description, sa chaîne de connexion ou ses informations d'identification.  
  
## Tâches et accès aux éléments  
 Lorsque vous créez des attributions de rôles, utilisez un rôle qui possède ces tâches pour affecter des autorisations appropriées aux utilisateurs et aux groupes.  
  
|Sélectionnez cette tâche|Pour autoriser les utilisateurs à effectuer les opérations suivantes|  
|----------------------|---------------------------------|  
|Afficher les sources de données|Afficher les éléments de source de données dans l'arborescence des dossiers. Sans cette tâche, l'élément n'est pas visible pour les utilisateurs et ils peuvent ignorer que la source de données est disponible.|  
|Gérer les sources de données|Afficher les propriétés qui spécifient le nom, la description et les informations de connexion. Cette tâche est également utilisée pour afficher un élément de source de données partagée dans la hiérarchie de dossiers. Si vous choisissez cette tâche, vous pouvez omettre la tâche « Afficher les sources de données ».|  
|Définir la sécurité au niveau des éléments|Créer et modifier des attributions de rôles qui contrôlent l'accès à la source de données partagée. Cette tâche doit être utilisée avec la tâche « Afficher les sources de données » ou avec la tâche « Gérer les sources de données ». Si tel n'est pas le cas, elle est sans effet puisque l'utilisateur ne peut pas sélectionner l'élément.|  
  
## Voir aussi  
 [Gérer des sources de données de rapports](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Dossiers sécurisés](../../reporting-services/security/secure-folders.md)   
 [Sécuriser des rapports et des ressources](../../reporting-services/security/secure-reports-and-resources.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Store Credentials in a Reporting Services Data Source](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  