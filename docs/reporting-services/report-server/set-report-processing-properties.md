---
title: "D&#233;finir les propri&#233;t&#233;s de traitement d&#39;un rapport | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rapports à la demande"
  - "traitement des rapports [Reporting Services], propriétés d'exécution"
  - "instantanés [Reporting Services], exécution des rapports"
  - "rapports mis en cache [Reporting Services]"
  - "instantanés de rapports [Reporting Services], exécution des rapports"
  - "instantanés d'exécution de rapport [Reporting Services]"
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# D&#233;finir les propri&#233;t&#233;s de traitement d&#39;un rapport
  Les propriétés d'exécution d'un rapport déterminent la façon dont le traitement du rapport s'effectue. Elles doivent être définies individuellement pour chaque rapport.  
  
 Pour définir les propriétés d'exécution d'un rapport, ouvrez le rapport dans le Gestionnaire de rapports, puis accédez à la page des propriétés d'exécution. Pour plus d’informations, consultez [Page de propriétés Options de traitement &#40;Gestionnaire de rapports&#41;](../Topic/Processing%20Options%20Properties%20Page%20\(Report%20Manager\).md). Vous pouvez également définir des propriétés via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Consultez [Page de propriétés Options de traitement &#40;Gestionnaire de rapports&#41;](../Topic/Processing%20Options%20Properties%20Page%20\(Report%20Manager\).md).  
  
## Modes d'exécution d'un rapport  
 Vous pouvez exécuter un rapport à la demande ou en tant qu'instantané. La section suivante décrit chaque méthode.  
  
### Exécution de rapports à la demande  
 Vous pouvez spécifier qu'un rapport interroge une source de données chaque fois qu'un utilisateur exécute le rapport, ce qui produit des rapports à la demande contenant des données actualisées. Une nouvelle instance du rapport est créée pour chaque utilisateur qui ouvre ou demande le rapport, de sorte que chaque nouvelle instance contient les résultats d'une nouvelle requête. Avec cette méthode, si dix utilisateurs ouvrent le rapport en même temps, dix requêtes sont envoyées à la source de données en vue d'un traitement.  
  
### Exécution de rapports à la demande à partir du cache  
 Afin d'améliorer les performances, vous pouvez spécifier qu'un rapport (et ses données) soit temporairement mis en cache lorsqu'un utilisateur l'exécute. La copie mise en cache est ensuite mise à la disposition des autres utilisateurs qui accèdent à ce même rapport. Avec cette méthode, si dix utilisateurs ouvrent le rapport, seule la première requête formulée aboutit au traitement du rapport. Le rapport est ensuite placé dans la mémoire cache pour être affiché par les neuf autres utilisateurs.  
  
 Les rapports mis en cache sont supprimés du cache aux intervalles que vous définissez. Vous pouvez spécifier des intervalles en minutes ou planifier une date et une heure spécifiques auxquelles vider le cache. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md).  
  
### Exécution de rapports à partir d'instantanés  
 Un instantané de rapport est un rapport contenant des informations de mise en page ainsi que des données qui sont extraites à un moment donné. Vous pouvez exécuter un rapport en tant qu'instantané de rapport afin d'éviter qu'il soit exécuté à des moments inopportuns (par exemple, pendant une sauvegarde programmée). En général, un instantané de rapport est créé et actualisé ultérieurement selon une planification, vous permettant ainsi de déterminer précisément le moment auquel le traitement du rapport et des données se produit. Si un rapport est basé sur des requêtes dont l'exécution est longue ou qui utilisent des données d'une source de données que vous ne souhaitez pas rendre accessible à certaines heures, vous devez exécuter le rapport en tant qu'instantané.  
  
 Un instantané de rapport est stocké dans une base de données du serveur de rapports, d'où il est ensuite extrait lorsqu'un utilisateur ou un processus (comme un abonnement) demande le rapport. Lorsqu'un instantané de rapport est mise à jour, elle est remplacée par une nouvelle instance. Le serveur de rapports ne conserve pas les versions antérieures d'un instantané de rapport sauf si vous définissez spécifiquement des options pour l'ajouter à l'historique de rapport. Pour plus d’informations, consultez [Créer, modifier et supprimer des instantanés dans l’historique de rapport](../../reporting-services/report-server/create-modify-and-delete-snapshots-in-report-history.md).  
  
 Les rapports ne sont pas tous configurables pour s'exécuter en tant qu'instantané. Vous ne pouvez pas créer l'instantané d'un rapport qui demande des informations d'identification aux utilisateurs ou qui utilise la sécurité intégrée de Windows pour obtenir les données du rapport. Si vous voulez exécuter un rapport paramétré en tant qu'instantané, vous devez spécifier un paramètre par défaut à utiliser lors de la création de l'instantané. Contrairement aux rapports qui s'exécutent à la demande, il est impossible, une fois le rapport ouvert, de définir une valeur de paramètre différente pour un instantané de rapport. Une telle possibilité se traduirait par une nouvelle requête de traitement du rapport, ce qui n'est pas autorisé.  
  
 Dans certains cas, la configuration d'un rapport à la demande pour qu'il s'exécute en tant qu'instantané peut désactiver les abonnements. Les circonstances suivantes entraînent un serveur de rapports à désactiver les abonnements existants qui ont été définis lorsque le rapport était configuré pour s'exécuter à la demande :  
  
-   Le rapport utilise des paramètres de requête et vous sélectionnez une valeur spécifique comme paramètre par défaut afin de répondre aux conditions d'exécution du rapport en tant qu'instantané.  
  
-   Les abonnements existants sont configurés pour utiliser des valeurs de paramètre qui diffèrent de celles que vous avez spécifiées par défaut pour l'instantané.  
  
 Lorsque ces conditions sont réunies, le serveur de rapports désactive l'abonnement dès qu'une planification prévoit son exécution. Pour réactiver l'abonnement, ouvrez-le, puis enregistrez-le. Lorsque vous ouvrez l'abonnement, le serveur de rapports met à jour les valeurs de paramètre de l'abonnement en utilisant celles spécifiées pour l'instantané. Pour plus d’informations sur les abonnements, consultez [Abonnements et remise &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## Voir aussi  
 [Définir les options de traitement &#40;Reporting Services en mode intégré SharePoint&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Configurer les propriétés d’exécution d’un rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)   
 [Concepts de Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Procédure : ajouter un instantané à un historique de rapport](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  