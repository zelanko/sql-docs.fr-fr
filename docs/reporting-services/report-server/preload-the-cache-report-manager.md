---
title: Précharger le Cache (SSRS) | Microsoft Docs
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6b2be1e020354f47aa21dc83f17ff6169bcf2d72
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66174993"
---
# <a name="preload-the-cache"></a>Précharger le cache  
  Vous pouvez précharger le cache pour un dataset partagé en créant un plan d'actualisation du cache pour le dataset partagé.  
  
 Vous pouvez précharger le cache pour un rapport de deux façons :  
  
1.  Créer un plan d'actualisation du cache pour le rapport. Cette méthode est recommandée.  
  
2.  Utilisez l'abonnement piloté par les données pour précharger des instances de rapports paramétrables dans le cache. Cette méthode était la seule permettant de précharger le cache dans les versions de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] antérieures à [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md).  
  
 Les conditions suivantes doivent être réunies avant de pouvoir mettre en cache un rapport ou un dataset partagé :  
  
-   La mise en cache doit être activée pour le dataset partagé ou le rapport.  
  
-   Les sources de données partagées pour le dataset partagé ou le rapport doivent être configurées pour utiliser des informations d'identification stockées ou aucune information d'identification.  
  
-   Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être en cours d’exécution.  
  
## <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a>Pour précharger le cache en créant un plan d'actualisation du cache  
  
1. Démarrez le [portail web d’un serveur de rapports](../../reporting-services/web-portal-ssrs-native-mode.md "Le portail web d’un serveur de rapports").  
  
2. Sélectionnez **Parcourir** à partir de l’écran d’accueil et naviguez dans l’arborescence des dossiers pour localiser l’élément que vous souhaitez mettre en cache.  
  
3. Sélectionnez les points de suspension dans le coin supérieur droit de l’élément, puis **Gérer** dans le menu déroulant.  
  
4. Sélectionnez l’onglet **Mise en cache** dans le menu vertical sur la gauche.  
  
5. Pour activer la mise en cache pour un jeu de données, sélectionnez la case d’option **Mettre en cache des copies de ce jeu de données et les utiliser en cas de disponibilité**. La section **Expiration du cache** apparaît alors sous celui-ci. Sélectionnez l'une des cases d'option suivantes :

    - **Le cache expire au bout de x minutes** (entrez le nombre de minutes pour x souhaité).
    - **Le cache expire selon une planification**.  Reporting Services fournit des planifications partagées et des planifications spécifiques aux rapports pour vous aider à contrôler le traitement, un contenu cohérent et les performances de la distribution des rapports. Pour plus d’informations, consultez [Créer, modifier et supprimer des planifications](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md "Créer, modifier et supprimer des planifications"). Vous disposez de plusieurs options sur la façon de créer une planification, dans ce cas pour l’expiration du cache : sélectionnez une des deux options de planification ci-dessous :  
      - Case d'option **Planification partagée**, puis sélectionnez une planification à partir de la zone de texte déroulante **Sélectionner une planification partagée**. Pour plus d’informations, consultez [Planifications](../../reporting-services/subscriptions/schedules.md "Planifications").  
      - Case d'option **Planification spécifique aux rapports**, puis sélectionnez le lien **Modifier la planification** si nécessaire pour afficher la page *Détails de la planification*.  

         ![La page des détails de planification d’expiration du cache de portail web pour les jeux de données](../../reporting-services/report-server/media/preload-the-cache/web-portal-dataset-cache-schedule-details.png "Page des détails de la planification de cache du jeu de données")

          Sur cette page, vous pouvez sélectionner :
         - Le type de planification :
           - **Heure** : exécution de la planification chaque : spécifiez les heures et minutes et l’heure de début.
           - **Jour** : sélectionnez une des trois options ci-dessous :  
              - **Les jours suivants** : (dim, lundi, mardi, mercredi, jeu, ven, sam).
              - **Tous les jours ouvrables**
              - **Répéter après ce nombre de jours** : spécifiez un nombre.  
           - **Semaine** : spécifiez les deux éléments suivants :
              - **Répéter après ce nombre de semaines** : spécifiez un nombre.  
              - **Les jours** : sélectionnez les jours de la semaine pour l’exécuter.  
           - **Mois** : le ou les mois, avec un choix de :
              - **La semaine du mois**,  
                 - Sélectionnez (1er, 2e, 3e, 4e ou dernière) dans la zone déroulante.  
                 - **Le jour de la semaine** pour l’exécuter. Sélectionnez une ou plusieurs cases à cocher (dim, lundi, mardi, mercredi, jeu, ven, sam).  
                 - **Le ou les jours du calendrier** : entrez le nombre de jours réel du mois séparés par des virgules ou une plage de jours séparés par un tiret ou n’importe quelle combinaison des deux (par exemple, 1,3-5).  
           - **Une fois** : une occurrence unique.  
         - **Heure de début** : l’heure du jour pour le démarrage de la planification.  
         - **Date de début et de fin** : spécifier la date de début et éventuellement la date de fin de la planification.
         - Sélectionnez **Appliquer** pour enregistrer la planification.  
           > [!NOTE]
           > Si la mise en cache n'est pas activée pour l'élément, vous serez invité à l'activer. Pour activer la mise en cache, sélectionnez **OK**.  

         - Sélectionnez **Créer le plan d’actualisation du cache** pour créer / enregistrer le plan du cache.  
         La page **Plans d’actualisation du cache** s’affiche à l’écran. À partir de là, vous pouvez :
           - Ajouter un nouveau plan d'actualisation du cache.
           - Créer un nouveau plan d’actualisation du cache à partir d’un plan existant.
           - Actualiser la page Plan d'actualisation du cache.
           - Supprimer un plan.
           - Rechercher un plan par nom.

         Si aucun plan d’actualisation du cache n’a encore été enregistré, la liste est vide et l’option « Ajouter » sera la seule disponible. Sélectionnez **+ Nouveau plan d’actualisation du cache** pour en ajouter un nouveau et la page **Nouveau plan d’actualisation du cache** s’affiche.  
           - Saisissez une **Description** dans la première zone de texte pour nommer le plan d’actualisation.  
           - Sélectionnez une des cases d’option suivantes dans **Actualiser le cache selon la planification suivante**  
             - **Planification partagée** : sélectionnez une planification partagée dans la zone déroulante adjacente. 
             - **Planification spécifique aux rapports** : modifiez la planification comme à l’étape 2.2 ci-dessus en sélectionnant le lien **Modifier la planification** si vous le souhaitez pour afficher la page *Détails de la planification*. 
             - Sélectionnez **Créer un plan d’actualisation du cache** pour enregistrer le plan, si vous l’ajoutez ou **Appliquer** si vous modifiez le plan.  
      Vous êtes redirigé vers la page **Plans d’actualisation du cache** mise à jour.
  
## <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a>Pour précharger le cache avec un rapport spécifique à l'utilisateur en utilisant un abonnement piloté par les données

1. Démarrez le [portail web d’un serveur de rapports](../../reporting-services/web-portal-ssrs-native-mode.md "Le portail web d’un serveur de rapports").  
2. Sélectionnez **Parcourir** à partir de l’écran d’accueil et naviguez dans l’arborescence des dossiers pour localiser le rapport auquel vous souhaitez vous abonner.  
3. Cliquez avec le bouton de droite sur le rapport, sélectionnez **S’abonner** dans le menu déroulant. La page **Nouveaux abonnements** s’affiche.  
4. Dans la zone de texte **Description**, saisissez une description de l’abonnement.  
5. La case d'option **Type d’abonnement** affiche deux options :  
   - **Abonnement standard** : pour générer et fournir un rapport
   - **Abonnement piloté par les données** : pour générer et fournir un rapport pour chaque ligne d'un jeu de données. Il s’agit de l’option que vous souhaitez sélectionner pour précharger le cache.
6. Dans la section **Planification**, sélectionnez une des cases d'option suivantes :
   - **Planification partagée** : sélectionnez une planification partagée dans la zone déroulante.  
   - **Planification spécifique aux rapports** : modifiez la planification comme à l’étape 2.2 ci-dessus en sélectionnant le lien **Modifier la planification** si vous le souhaitez pour afficher la page *Détails de la planification*.  
7. La section **Destination** affiche les choix suivants dans une zone déroulante :
    - **Partage de fichiers Windows**
    - **E-mail**
    - **Fournisseur de remise de Null** : pour cette tâche, sélectionnez le fournisseur de remise Null.  
8. Dans la section **Jeu de données**, modifiez ou créez un jeu de données pour cet abonnement à un rapport en sélectionnant le bouton **Modifier le jeu de données**.  
9. Sur la page **Modifier le jeu de données**, dans la section **source de données**, choisissez la source de données qui contient les valeurs des paramètres du rapport et les options de remise. Les choix sont les suivants :  
   - **Une source de données partagée** : sélectionnez les points de suspension et sélectionnez une source de données partagée dans le dossier *Source de données partagée*.
   - **Une source de données personnalisée** : la plus probable. il s’agit d’une option à sélectionner, à moins que vous ou une autre personne ayez déjà suivi les étapes ci-dessous pour la créer en tant que source de données partagée.  
     - Spécifiez le type de connexion, la chaîne de connexion et les informations d'identification pour accéder à la source de données contenant les données des abonnés. L’exemple suivant décrit une chaîne de connexion utilisée pour se connecter à des abonnés nommés d’une base de données SQL Server.  
  
   ```T-SQL
   data source=<servername>;initial catalog=Subscribers  
   ```
  
10. Dans la section **Requête** : spécifiez la requête qui récupère les données d’abonné souhaitées.  Par exemple :  
  
    ```T-SQL  
    Select * from RptSubscribers  
    ```
  
    Augmentez éventuellement le délai d'attente des requêtes dont le traitement est long.  
  
11. Sélectionnez **Valider**. La requête doit être validée pour pouvoir continuer. Lorsque le message **Validation réussie** s’affiche, une liste de champs de Jeux de données s’affiche sous le bouton **Valider**. Sélectionnez **Appliquer** pour créer la source de données personnalisées.  
  
12. Vous êtes redirigé vers la page **Nouvel abonnement**.  Dans la section **Paramètres du rapport**, spécifiez les valeurs de paramètres du rapport pour les paramètres du rapport affichés, le cas échéant.  

13. Sélectionnez **Créer l'abonnement**.  
  
14. La page **Abonnements** s’affiche avec votre nouvel abonnement piloté par les données. À partir de cette page, vous pouvez activer l’abonnement lorsque vous êtes prêt, en cochant la case à gauche de celui-ci et en sélectionnant le bouton **Activer**. ![bouton Activer de la page Abonnements](../../reporting-services/report-server/media/preload-the-cache/subscriptions-page-enable-button.png "Le bouton Activer de la page Abonnements")

15. Précisez le moment où l'abonnement doit être traité. Ne choisissez pas l’option **Lorsque les données du rapport sont mises à jour sur le serveur de rapports**. Elle est réservée exclusivement aux instantanés. Si vous voulez utiliser une planification préexistante, sélectionnez **Suivant une planification partagée**.  
  
     Ou, pour créer une planification personnalisée, sélectionnez **Suivant une planification créée pour cet abonnement**, puis **Suivant**. Configurez la planification, puis sélectionnez **Terminer**.  
  
    > [!NOTE]  
    > Pour que les abonnés reçoivent la version du rapport la plus récente, la planification que vous configurez doit être chronologiquement cohérente par rapport à la planification de la remise du rapport que vous avez définie pour les abonnés. Pour plus d’informations, consultez le [portail web d’un serveur de rapports](../../reporting-services/web-portal-ssrs-native-mode.md  "Le portail web d’un serveur de rapports").  
  
16. Configurez les options d'exécution du rapport comme suit. Dans la page du rapport, sélectionnez l’onglet **Propriétés**.  
  
17. Dans le cadre de gauche, sélectionnez l’onglet **Exécution**.  
  
18. Dans la page qui s’affiche, sélectionnez **Effectuer le rendu de ce rapport avec les données les plus récentes**.  
  
19. Choisissez l'une des deux options de mise en cache suivantes et configurez l'expiration comme suit :  
  
    - Pour qu’une copie en cache expire à la fin d’une période donnée, sélectionnez **Mettre en cache une copie temporaire du rapport. Faire expirer la copie du rapport après un certain nombre de minutes.** Tapez le nombre de minutes pour l'expiration du rapport.  
  
    - Pour qu’une copie en cache expire selon une planification, sélectionnez **Mettre en cache une copie temporaire du rapport. Faire expirer la copie du rapport selon la planification suivante.** Sélectionnez **Configurer** ou sélectionnez une planification partagée pour définir une planification pour l’expiration du rapport.  
  
20. Sélectionnez **Appliquer**.
  
## <a name="see-also"></a>Voir aussi  

 [Abonnements pilotés par les données](../../reporting-services/subscriptions/data-driven-subscriptions.md)  
 [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
 [Performances, instantanés, mise en cache &#40;Reporting Services&#41;](../../reporting-services/report-server/performance-snapshots-caching-reporting-services.md)  
 [Définir les propriétés de traitement d'un rapport](../../reporting-services/report-server/set-report-processing-properties.md)  
 [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
 [Utilisation de jeux de données partagés](../../reporting-services/work-with-shared-datasets-web-portal.md)  
  
