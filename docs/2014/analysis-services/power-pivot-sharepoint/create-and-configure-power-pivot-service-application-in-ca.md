---
title: Créer et configurer une application de service PowerPivot dans l’administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e5693e-4af3-453f-83f3-07481ab1ac6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64997cb3db784ea78a72a7c812c8f88034c2358d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071581"
---
# <a name="create-and-configure-a-powerpivot-service-application-in-central-administration"></a>Créer et configurer une application de service PowerPivot dans l'Administration centrale
  Une application de service PowerPivot est une instance de service partagé du service système PowerPivot. Chaque application de service possède une identité d'application, des paramètres de configuration, des propriétés et un système de stockage des données internes qui lui sont propres.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Déterminer s'il est nécessaire de créer une nouvelle application de service PowerPivot](#determine)  
  
 [Créer une application de service PowerPivot](#CreateApp)  
  
 [Configurer l'application de service PowerPivot](#ConfigApp)  
  
 [Affecter une application de service PowerPivot à une application Web](#AssignGSA)  
  
 [Modifier les propriétés d'une application de service](#EditGSA)  
  
##  <a name="determine-whether-to-create-a-new-powerpivot-service-application"></a><a name="determine"></a>Déterminer si une nouvelle application de service PowerPivot doit être créée  
 Dans une installation PowerPivot pour SharePoint, la batterie de serveurs doit inclure au moins une application de service PowerPivot. Une application de service est automatiquement créée si vous avez utilisé l'outil de configuration de PowerPivot pour configurer le serveur. Sinon, vous devez créer une application de service PowerPivot manuellement dans l'Administration centrale.  
  
 Lorsque vous créez une application de service, le service devient disponible et la base de données d'application de service est générée. En fonction des options que vous sélectionnez lors de la création de l'application de service, une connexion au service PowerPivot est ajoutée au groupe de connexions de service par défaut. Toutes les applications Web SharePoint qui s'abonnent au groupe de connexions de service par défaut bénéficient automatiquement d'un accès immédiat à l'application de service PowerPivot.  
  
 Vous pouvez créer plusieurs applications de service PowerPivot. Bien qu'une application de service soit suffisante dans la plupart des scénarios de déploiement, vous pouvez créer une application de service PowerPivot supplémentaire si les critères suivants sont essentiels pour votre entreprise :  
  
-   Utilisation d'un compte d'actualisation des données PowerPivot sans assistance différent pour chaque application.  
  
-   Utilisation de différents délais d'attente, historiques d'utilisation et seuils pour la création des rapports de réponses aux requêtes.  
  
-   Délégation de l'administration du service à différentes personnes. Un administrateur peut consulter l'historique d'actualisation des données, les données d'utilisation et d'autres propriétés, uniquement pour l'application qu'il administre. Si vous êtes dans l'obligation d'isoler les données de différentes applications Web SharePoint (par exemple, si votre société est un service d'hébergement qui doit garantir l'isolation des données pour les applications Web SharePoint qui appartiennent à des clients différents), créer des applications de service PowerPivot distinctes vous permet de répondre à ces besoins d'isolation en garantissant que chaque administrateur de service consulte uniquement les paramètres de configuration et les propriétés de l'application qu'il gère.  
  
 La création d'une application de service supplémentaire entraîne de nouveaux besoins en gestion d'associations de services. À savoir, cela nécessite de créer et d'utiliser des listes d'association de services personnalisées pour chaque application de service supplémentaire créée.  
  
 Si vous n'avez pas de raison particulière de créer une application de service PowerPivot supplémentaire, vous devez utiliser une seule application de service pour toutes les applications Web dans la batterie de serveurs.  
  
##  <a name="create-a-powerpivot-service-application"></a><a name="CreateApp"></a>Créer une application de service PowerPivot  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Dans le ruban **Applications de service** , cliquez sur **Nouveau**.  
  
3.  Sélectionnez **SQL Server application de service PowerPivot**. Si cette option ne s'affiche pas dans la liste, cela signifie que PowerPivot pour SharePoint n'est pas installé ou configuré correctement.  
  
4.  Dans la page **créer une application de service PowerPivot** , entrez un nom pour l’application. La valeur par défaut\<est PowerPivotServiceApplication Number>. Si vous créez plusieurs applications de service PowerPivot, il est utile d'entrer un nom descriptif pour permettre aux autres administrateurs de savoir comment l'application est utilisée.  
  
5.  Dans Pool d'applications, créez un nouveau pool d'applications pour l'application (recommandé). Sélectionnez ou créez un compte géré pour le pool d'applications. Veillez à spécifier un compte d'utilisateur de domaine. Un compte d'utilisateur de domaine permet l'utilisation de la fonctionnalité Compte géré de SharePoint, qui vous permet de mettre à jour des mots de passe et des informations sur le compte dans un seul emplacement. Des comptes de domaine sont requis si vous prévoyez une montée en puissance parallèle du déploiement incluant des instances de service supplémentaires qui s'exécuteront sous la même identité.  
  
6.  Dans **Serveur de base de données**, la valeur par défaut est l'instance du moteur de base de données SQL Server qui héberge les bases de données de configuration de la batterie de serveurs. Vous pouvez utiliser ce serveur ou choisir un autre serveur SQL Server.  
  
7.  Dans **nom de la base de données**, la\<valeur par défaut est PowerPivotServiceApplication1_ GUID>. Vous devez créer une base de données unique pour chaque application de service PowerPivot. Le nom de la base de données par défaut correspond au nom par défaut de l'application de service. Si vous avez entré un nom d'application de service unique, suivez une convention d'affectation des noms similaire pour la base de données afin de pouvoir les gérer ensemble.  
  
8.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez **Authentification SQL**, reportez-vous au guide de l'administrateur SharePoint pour des recommandations concernant l'utilisation de ce type d'authentification dans un déploiement SharePoint.  
  
9. Si vous le souhaitez, activez la case à cocher **Ajouter le proxy de cette application de service PowerPivot au groupe de proxy par défaut de la batterie de serveurs.** Cette option permet d'ajouter la connexion à l'application de service au groupe de connexions de service par défaut.  
  
     Vous devez activer cette case à cocher si vous créez votre première application de service PowerPivot. Le groupe de connexions par défaut doit contenir une application de service PowerPivot pour que le Tableau de bord de gestion PowerPivot fonctionne correctement.  
  
     N'ajoutez pas l'application de service PowerPivot au groupe de connexions par défaut s'il en existe déjà une. L'ajout de plusieurs entrées du même type d'application de service n'est pas une configuration prise en charge et risque de provoquer des erreurs. Si vous créez des applications de service supplémentaires, laissez-les hors du groupe de connexions par défaut et ajoutez-les plutôt à des listes personnalisées.  
  
     Pour plus d’informations sur les associations de service, consultez [connecter une application de service PowerPivot à une application Web SharePoint dans l’administration centrale](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
10. Cliquez sur **OK**. Le service s'affiche avec les autres services gérés dans la liste des applications de service de la batterie de serveurs.  
  
##  <a name="configure-powerpivot-service-application"></a><a name="ConfigApp"></a>Configurer l’application de service PowerPivot  
 Une application de service PowerPivot est créée à l'aide d'une configuration par défaut. Les paramètres par défaut sont recommandés dans la plupart des scénarios. Modifiez-les uniquement si vous constatez des temps de réponse longs ou des suppressions de connexions, ou si vous changez la configuration de service PowerPivot pour des applications Web SharePoint spécifiques.  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
     Dans la liste des applications de service, vous devez voir l'application de service que vous venez de créer et de nommer. La valeur par défaut est **PowerPivotServiceApplication1**.  
  
2.  Cliquez sur l'application de service PowerPivot. Cette opération ouvre le tableau de bord de gestion PowerPivot.  
  
3.  Dans la liste **Actions** située dans l'angle supérieur droit du tableau de bord, cliquez sur **Configurer les paramètres d'application de service**.  
  
4.  Dans **délai de chargement de la base de données**, augmentez ou diminuez la valeur pour modifier la durée pendant laquelle le service PowerPivot attend une réponse de l’instance de SQL Server Analysis Services (PowerPivot) à laquelle il a transféré une demande de chargement de données. Étant donné que l'acheminement sur le réseau des datasets très volumineux prend du temps, vous devez accorder à l'instance de service PowerPivot suffisamment de temps pour récupérer le classeur Excel et déplacer les données PowerPivot vers une instance d'Analysis Services pour le traitement de la requête. Étant donné que les données PowerPivot peuvent être particulièrement volumineuses, la valeur par défaut est 30 minutes.  
  
5.  Dans **Délai d'attente du pool de connexions**, augmentez ou diminuez la valeur afin de modifier le nombre de minutes pendant lesquelles une connexion de données inactive restera ouverte. La valeur par défaut est 30 minutes. Durant ce laps de temps, le service PowerPivot réutilise une connexion de données inactive pour les demandes en lecture seule provenant du même utilisateur SharePoint pour les mêmes données PowerPivot. Si aucune demande supplémentaire n'est reçue pour ces données pendant la période spécifiée, la connexion est supprimée du pool. Les valeurs valides sont comprises entre 1 et 3600 secondes. Pour plus d’informations sur les pools de connexions, consultez [référence des paramètres de Configuration &#40;PowerPivot pour SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md).  
  
6.  Dans **taille maximale du pool**de connexions utilisateur, augmentez ou diminuez la valeur pour modifier le nombre maximal de connexions inactives que le service PowerPivot créera dans les pools de connexions pour chaque utilisateur SharePoint, DataSet PowerPivot et combinaisons de versions.  
  
     La valeur par défaut est 1000 connexions inactives. Les valeurs valides sont -1 (illimité), 0 (désactive le regroupement de connexions utilisateur) ou une plage comprise entre 1 et 10000.  
  
     Ces pools de connexions permettent au service de gérer plus efficacement les connexions aux mêmes données en lecture seule par le même utilisateur. Si vous désactivez le regroupement de connexions, chaque connexion sera recréée.  
  
     Notez que la modification de la limite de taille du pool de connexions, y compris son paramétrage sur la valeur 0, ne provoque pas de perte de connexion. Les pools de connexions servent à réduire les temps d'attente lors de la connexion aux données. Le service PowerPivot ne refuse jamais une connexion reposant sur les paramètres du pool de connexions.  
  
7.  Dans **taille maximale du pool de connexions d’administration**, augmentez ou diminuez la valeur afin de modifier le nombre de connexions ouvertes dans un pool de connexions créé pour une connexion de service PowerPivot à Analysis Services. Chaque instance de service PowerPivot ouvre une connexion d'administration distincte à une instance d'Analysis Services sur le même ordinateur. Le service PowerPivot crée un pool distinct pour réutiliser les connexions d'administration en vue de vérifier si des connexions sont inactives et de contrôler l'intégrité du serveur. La valeur par défaut est 200 connexions. Les valeurs valides sont -1 (illimité), 0 (désactive le regroupement de connexions administrateur) ou 1 à 10000. Si vous sélectionnez 0, chaque connexion est recréée.  
  
8.  Dans **méthode d’allocation**, vous pouvez spécifier le schéma d’équilibrage de charge que le service système PowerPivot utilise pour sélectionner une application de service PowerPivot spécifique pour l’équilibrage de charge d’une demande initiale. La valeur par défaut est **Selon l'intégrité**pour allouer les demandes en fonction de l'état du serveur, mesuré d'après la mémoire disponible et l'utilisation du processeur. Alternativement, vous pouvez choisir la méthode **Tourniquet (round robin)** , laquelle alloue les demandes aux serveurs dans le même ordre de répétition, qu'un serveur soit occupé ou inactif.  
  
9. Dans Actualisation des données, sous **Heures d'ouverture**, vous pouvez spécifier la plage d'heures qui détermine un jour ouvrable. Les planifications d'actualisation des données peuvent s'exécuter à la fin d'une journée de travail pour récupérer les données transactionnelles qui ont été générées pendant les heures d'ouverture normales.  
  
10. Dans le **compte d’actualisation des données PowerPivot sans assistance**, vous pouvez spécifier une application service Banque d’informations sécurisé cible prédéfinie qui stocke un compte prédéfini pour l’exécution des travaux d’actualisation des données PowerPivot. Veillez à spécifier le nom de l'application cible, et pas l'ID. L'application cible pour l'actualisation des données sans assistance est créée automatiquement si vous avez utilisé l'option Nouveau serveur dans le programme d'installation de SQL Server pour installer PowerPivot pour SharePoint. Sinon, vous devez créer l'application cible manuellement. Pour obtenir des instructions sur la configuration du compte, consultez [configurer le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
11. Dans **Autoriser les utilisateurs à entrer des informations d'identification Windows personnalisées**, vous pouvez activer ou désactiver la case à cocher pour spécifier si les propriétaires de planifications peuvent entrer des informations d'identification Windows arbitraires pour exécuter une planification d'actualisation des données. Si vous activez cette case à cocher, l'application de service PowerPivot crée et gère une application cible pour chaque ensemble d'informations d'identification stockées. Pour plus d’informations, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
12. Dans **Longueur maximale de l'historique de traitement**, vous pouvez spécifier la durée de rétention d'un enregistrement d'historique du traitement de l'actualisation des données. Ces informations s'affichent dans les pages d'historique de l'actualisation des données qui sont conservées pour chaque classeur utilisant l'actualisation des données. Elles s'affichent également dans le tableau de bord de gestion PowerPivot.  
  
13. Dans Collecte des données d'utilisation, sous **Intervalle de création de rapports de requête**, spécifiez une fréquence pour la création de rapports liés aux statistiques sur les requêtes. Les statistiques sur les requêtes sont générées comme un événement unique pour minimiser les communications de serveur à serveur.  
  
14. Dans Historique des données d'utilisation, spécifiez la durée de rétention d'un enregistrement d'historique des données d'utilisation. Les informations d'utilisation s'affichent dans le Tableau de bord de gestion PowerPivot. Les rapports sont moins efficaces si vous spécifiez une valeur trop basse pour l'historique des données de l'utilisation.  
  
15. Dans Collecte des données d'utilisation, pour chaque seuil de réponse aux requêtes, spécifiez une limite maximale qui détermine la fin d'une catégorie et le début d'une autre. Ces catégories établissent une référence par rapport à laquelle chaque comportement de requête est mesuré. Vous pouvez utiliser ces catégories pour analyser les tendances constatées en termes de temps de réponse aux requêtes pour votre système. Ces informations s'affichent dans le tableau de bord de gestion PowerPivot.  
  
16. Cliquez sur **OK** pour enregistrer vos modifications.  
  
     Les modifications apportées au délai de chargement ou à la méthode d'allocation sont appliquées uniquement aux nouvelles requêtes entrantes. Les requêtes qui sont déjà en cours de traitement sont soumises aux valeurs qui étaient appliquées lors de la réception de la requête.  
  
##  <a name="assign-a-powerpivot-service-application-to-a-web-application"></a><a name="AssignGSA"></a>Affecter une application de service PowerPivot à une application Web  
 Une fois que vous avez configuré une application de service PowerPivot, vous pouvez l'affecter à une application Web. Pour ce faire, vous devez l'ajouter à la liste des connexions d'application de service de cette application Web. Il existe deux façons d'effectuer cette opération :  
  
-   Ajoutez-la au groupe de connexions **par défaut** . Le *groupe de connexions par défaut* est une collection de connexions d'application de service qui sont disponibles pour toute application Web y faisant référence. Vous devez ajouter une application de service PowerPivot à cette liste.  
  
-   Créez une liste de connexions **personnalisée** pour une application Web spécifique. Si vous avez créé plusieurs applications de service PowerPivot, vous pouvez choisir l'application à utiliser en la sélectionnant dans une liste personnalisée.  
  
 Le groupe de connexions par défaut accepte plusieurs applications de service du même type. Cependant, sachez qu'ajouter plusieurs applications de service PowerPivot à cette liste n'est pas une configuration prise en charge.  
  
1.  Dans Administration Centrale, sous **Gestion des applications**, cliquez sur **Gérer les applications Web**.  
  
2.  Sélectionnez l'application pour laquelle vous voulez affecter une connexion (par exemple, SharePoint -80).  
  
3.  Cliquez sur **Connexions de service**.  
  
4.  Dans **modifier le groupe d’associations suivant**, sélectionnez **par défaut** ou **[personnalisé]**.  
  
5.  Pour **[personnalisé]**, activez la case à cocher en regard de chaque connexion d’application de service que vous souhaitez utiliser. Si vous avez plusieurs applications de service PowerPivot (indiquées par type défini `PowerPivot Service Application Proxy`sur), veillez à en choisir une seule.  
  
6.  Cliquez sur **OK**.  
  
##  <a name="edit-service-application-properties"></a><a name="EditGSA"></a>Modifier les propriétés d’une application de service  
 Suivez les instructions ci-dessous pour rouvrir la page de propriétés qui spécifie le nom de l'application de service, le pool d'applications, les paramètres de base de données et les associations de service.  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Sélectionnez, mais sans cliquez dessus, l'application de service PowerPivot. Vous pouvez cliquer sur le nom de type pour sélectionner la ligne entière.  
  
3.  Cliquez sur **Propriétés** dans le ruban.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
