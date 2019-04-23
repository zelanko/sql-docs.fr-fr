---
title: Créer la Page abonnement piloté par les données (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 814b4653-572a-48c7-847f-b310ba0f3046
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 625afedabdb376f913d3353e2bda343bba66e3e1
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59964815"
---
# <a name="create-data-driven-subscription-page-report-manager"></a>Page Créer un abonnement piloté par les données (Gestionnaire de rapports)
  Les pages Créer un abonnement piloté par les données vous permettent de générer ou modifier un abonnement qui interroge une base de données de l'abonné pour obtenir des informations sur l'abonnement chaque fois que l'abonnement est exécuté. Les abonnements pilotés par les données utilisent les résultats de la requête pour identifier les destinataires de l'abonnement, paramètres de remise et valeurs des paramètres de rapport. Lors de l'exécution, le serveur de rapports exécute une requête pour obtenir les valeurs utilisées pour les paramètres de l'abonnement. Vous pouvez utiliser ces pages pour définir la requête et attribuer des valeurs de requête aux paramètres de l'abonnement. Les valeurs et les options que vous spécifiez pour un abonnement piloté par les données sont réparties dans plusieurs pages (identiques à celles d'un Assistant). Il existe sept pages en tout.  
  
 Pour créer un abonnement piloté par les données, vous devez savoir comment écrire une requête ou une commande qui permet d'obtenir les données pour l'abonnement. Vous devez également avoir une banque de données qui contient les données d'abonné (par exemple, les noms et adresses de messagerie des abonnés) à utiliser pour l'abonnement.  
  
 Cette page est disponible pour les utilisateurs qui disposent d'autorisations avancées. Si vous utilisez la sécurité par défaut, les abonnements pilotés par les données ne peuvent pas être utilisés pour les rapports contenus dans le dossier Mes rapports.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-data-driven-subscription-page"></a>Pour ouvrir la page Abonnement piloté par les données  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez créer un abonnement piloté par les données.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés **générales** pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Abonnements** , puis cliquez sur **Nouvel abonnement piloté par les données**.  
  
    > [!NOTE]  
    >  Pour que ce bouton soit activé, la source de données du rapport doit utiliser les informations d'identification stockées.  
  
## <a name="start-a-subscription-page-1"></a>Création d'un abonnement (page 1)  
 **Description**  
 Fournit une description de l'abonnement. Cette description apparaît dans les listes d'abonnements, sous **Mes abonnements** et l'onglet **Abonnements** du rapport.  
  
 **Spécifiez le mode de notification des destinataires**  
 Sélectionnez l'extension de remise à utiliser pour distribuer le rapport. Une seule extension de remise peut être utilisée pour chaque abonnement. Les options suivantes sont disponibles :  
  
-   Sélectionnez **Partage de fichiers du serveur de rapports** pour remettre les rapports à un partage de fichiers. Le rapport sera remis en tant que fichier statique, déconnecté du serveur de rapports. Pour plus d’informations, voir [File Share Delivery in Reporting Services](subscriptions/file-share-delivery-in-reporting-services.md).  
  
-   Sélectionnez **Messagerie Report Server** pour remettre les rapports à une boîte de réception de messagerie. Pour plus d’informations, voir [E-Mail Delivery in Reporting Services](subscriptions/e-mail-delivery-in-reporting-services.md).  
  
-   Sélectionnez **Fournisseur de remise Null** pour remettre les rapports à la base de données du serveur de rapports. Cette option crée des instantanés de rapport. Choisissez cette option lorsque vous souhaitez précharger le serveur de rapports avec des instantanés de rapport spécifiques à l'utilisateur ou paramétrés, suivant une planification spécifique. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md).  
  
 **Spécifiez une source de données qui contient les informations de destinataire**  
 Spécifiez la définition de la connexion à la source de données. Vous pouvez choisir une source de données partagée si vous en possédez une qui contient les informations de connexion dont vous avez besoin. Vous pouvez également spécifier ces informations directement dans cet abonnement.  
  
 La source de données fournit les données des abonnés. Il peut s'agir de noms d'employés, d'ID d'employés, d'adresses de messagerie et de préférences relatives aux formats d'exportation (tels que HTML ou PDF). Si vous utilisez l'extension de remise par messagerie du serveur de rapports, la source de données doit contenir des adresses de messagerie.  
  
## <a name="specify-a-connection-page-2"></a>Spécification d'une connexion (page 2)  
 Si vous spécifiez une source de données partagée, utilisez cette page pour sélectionner un élément de source de données partagée. Vous pouvez utiliser l'arborescence pour naviguer jusqu'à l'élément et le sélectionner. Si vous définissez une connexion pour cet abonnement, utilisez cette page pour spécifier les options suivantes :  
  
 **Type de connexion**  
 Sélectionnez quelle extension de traitement de données à utiliser avec la source de données.  
  
 **Chaîne de connexion**  
 Tapez une chaîne de connexion à utiliser pour vous connecter à la source de données.  
  
 **Se connecter à l’aide de**  
 Tapez les informations d'identification à utiliser lors de la connexion à la source de données. Les informations d'identification sont stockées sous forme de valeurs chiffrées dans la base de données du serveur de rapports.  
  
 Si la source de données utilise l'authentification Windows, sélectionnez **Utiliser comme informations d'identification Windows** lorsque vous spécifiez la connexion.  
  
 Si vous utilisez une source de données qui n'authentifie pas les connexions utilisateur (par exemple, si la source de données est un fichier XML), sélectionnez Informations d'identification non requises. Cette option requiert que vous ayez précédemment configuré le compte d'exécution sans assistance. Pour plus d’informations, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## <a name="specify-a-query-page-3"></a>Spécification d'une requête (page 3)  
 Utilisez cette page pour entrer la requête qui récupère les données d'abonné. Pour un résultat optimal, exécutez d'abord la requête dans SQL Server Management Studio avant de l'utiliser dans l'abonnement piloté par les données. Vous pouvez ensuite examiner les résultats pour vérifier qu'ils contiennent les informations requises. Les points importants à noter sur les résultats de la requête sont les suivants :  
  
-   Les colonnes dans le jeu de résultats déterminent les valeurs que vous pouvez spécifier pour les options de remise et les paramètres de rapport. Par exemple, si vous créez un abonnement piloté par les données pour la remise par messagerie électronique, vous devez avoir une colonne d'adresses de messagerie.  
  
-   Les lignes dans le jeu de résultats déterminent le nombre de remises de rapports générées. Si vous avez 10 000 lignes, le serveur de rapports générera 10 000 notifications et remises.  
  
 **Requête**  
 Spécifiez une requête SQL ou une commande qui permet d'extraire un jeu de résultats qui contient une ligne pour chaque destinataire de l'abonnement. Dans les pages suivantes, l'ensemble de résultats est utilisé pour remplir les paramètres d'extension pilotés par les données.  
  
 **Délai d'expiration**  
 Spécifiez une valeur de délai d'expiration de requête. Cette valeur doit être suffisamment importante pour terminer le traitement de la requête.  
  
 **Valider**  
 Cliquez sur **Valider** pour vérifier la requête. La requête doit générer des résultats valides pour que vous puissiez continuer. Si vous ne cliquez pas sur **Valider**, la requête est validée lorsque vous cliquez sur **Suivant**.  
  
## <a name="set-delivery-options-page-4"></a>Définition d'options de remise (page 4)  
 Dans la quatrième page, vous devez spécifier les options des extensions de remise. Les options qui apparaissent dans la page sont dérivées de l'extension de remise. La façon dont vous spécifiez ces options peut varier considérablement selon leur présentation par l'extension de remise. Si l'extension ne contient aucun paramètre, aucune option n'apparaît dans cette page.  
  
|Sélectionnez cette option|Pour effectuer cette opération|  
|-----------------|----------------|  
|**Spécifier une valeur statique**|Utiliser une valeur de constante pour le paramètre de remise. Certaines extensions de remise fournissent des valeurs statiques que vous pouvez sélectionner. Par exemple, la remise par courrier électronique à un serveur de rapports fournit des valeurs pour **Inclure un rapport**, **Format du rendu**, **Priorité**et **Inclure un lien**.|  
|**Obtenir la valeur de la base de données**|Utiliser une valeur du jeu de résultats. Les colonnes du jeu de résultats peuvent être utilisées pour fournir des données d'abonné et des valeurs des paramètres de rapport.|  
|**Aucune valeur**|Omettre le paramètre de l'abonnement.|  
  
#### <a name="set-delivery-options-for-file-share-delivery"></a>Définition des options de remise pour la remise par partage de fichiers  
 L'extension de remise par partage de fichiers est souvent utilisée, car elle ne requiert aucune configuration au préalable. Si vous l'utilisez, le tableau suivant décrit les options que vous pouvez définir :  
  
 **Nom de fichier**  
 Spécifie le nom de fichier du rapport. L'extension de remise par partage de fichiers remet un rapport en tant que fichier d'application statique dans un dossier partagé. Dans la plupart des cas, vous devez utiliser une valeur de la base de données pour créer le nom de fichier. Selon la façon dont vous définissez le mode écriture, l'utilisation d'une valeur statique provoquera le remplacement de la remise précédente par chaque nouvelle remise.  
  
 **Chemin d'accès**  
 Spécifiez un dossier partagé accessible via une connexion réseau. Pour vérifier que le dossier est accessible, cliquez sur **exécuter** dans le menu Démarrer et entrez le chemin du dossier dans ce format : \\ \\< nom_ordinateur\>\\< NomDossierPartagé\>.  
  
 **Format de rendu**  
 Spécifiez le format de sortie du fichier. Le serveur de rapports peut écrire le fichier dans des formats d'application des extensions de rendu installées sur le serveur de rapports.  
  
 **Mode écriture**  
 Spécifiez si le serveur de rapports doit remplacer un fichier par une version plus récente, l'incrémenter ou supprimer la remise si un fichier du même nom est trouvé.  
  
 **Extension de fichier**  
 Spécifiez True pour ajouter une extension de fichier qui correspond au format de rendu que vous avez sélectionné.  
  
 **Nom d'utilisateur**  
 Entrez le compte d’utilisateur de domaine qui a l’autorisation d’ajouter des fichiers dans le dossier partagé au format suivant : \<domaine >\\< nom d’utilisateur\>.  
  
 **Mot de passe**  
 Entrez le mot de passe du compte.  
  
## <a name="set-parameters-page-5"></a>Définition de paramètres (page 5)  
 Si un rapport contient des paramètres, vous devez spécifier les valeurs de paramètres à utiliser. Les valeurs de paramètres peuvent être obtenues à partir de la source de données de l'abonné (par exemple, si vous possédez un rapport sur les ventes régionales paramétré sur base d'un code de région, vous pouvez obtenir des informations de région pour chaque employé si celles-ci sont stockées dans la base de données de l'employé).  
  
|Sélectionnez cette option|Pour effectuer cette opération|  
|-----------------|----------------|  
|**Spécifier une valeur statique**|Utiliser une valeur de constante pour le paramètre si vous souhaitez utiliser le même paramètre pour tous les abonnés. Si le paramètre comporte plusieurs valeurs, vous pouvez choisir une valeur dans la liste.|  
|**Par défaut**|Certains rapports contiennent une valeur par défaut pour l'ensemble ou certains des paramètres. Si le paramètre de rapport a une valeur par défaut, cliquez sur cette case à cocher pour l'utiliser.|  
|**Obtenir la valeur de la base de données**|Utiliser une valeur du jeu de résultats. Les colonnes du jeu de résultats peuvent être sélectionnées comme une source d'une valeur de données à utiliser avec chaque instance d'abonnement.|  
  
## <a name="specify-a-trigger-page-6"></a>Spécification d'un déclencheur (page 6)  
 Sélectionnez un événement qui démarre le traitement des abonnements.  
  
|Sélectionnez cette option|Pour effectuer cette opération|  
|-----------------|----------------|  
|**Lorsque les données du rapport sont mis à jour sur le serveur de rapports**|Si le rapport est configuré pour s'exécuter comme un instantané d'exécution de rapport, vous pouvez spécifier que l'abonnement est exécuté lorsque l'instantané est actualisé.|  
|**Suivant une planification créée pour cet abonnement**|Exécuter l'abonnement à une date et une heure spécifiques.|  
|**Suivant une planification partagée**|Exécuter l'abonnement à l'aide des informations de planification fournies par l'intermédiaire d'une planification partagée.|  
  
## <a name="schedule-a-subscription-page-7"></a>Planification d'un abonnement (page 7)  
 Si vous planifiez l'abonnement, vous devez spécifier la fréquence de remise du rapport. Le premier ensemble d'options spécifie une catégorie de fréquences (toutes les heures, tous les jours, toutes les semaines, etc.) Le second ensemble d'options qui apparaît dépend de votre sélection initiale.  
  
 **Toutes les heures**  
 Définit une planification qui s'exécute toutes les heures.  
  
 **Quotidienne**  
 Définit une planification qui s'exécute les jours sélectionnés à une heure spécifique. Vous pouvez spécifier les jours comme suit : Chaque  *\<jour >*, tous les jours ouvrables et chaque  *\<nombre >* jours. La sélection d'une option rend les autres inapplicables même si d'autres jours semblent sélectionnés.  
  
 **Hebdomadaire**  
 Définit une planification qui s'exécute de façon hebdomadaire à une heure spécifique. L'intervalle peut correspondre à des semaines entières (toutes les deux semaines, par exemple) ou à des jours compris dans la semaine.  
  
 **Mensuel**  
 Définit une planification qui s'exécute tous les mois. Dans un mois, vous pouvez choisir un jour basé sur un modèle (le dernier dimanche de chaque mois, par exemple) ou des dates spécifiques (tels que 1 et 15 pour indiquer le 1er et le 15e jour de chaque mois). À l'aide de virgules et de tirets, vous pouvez spécifier plusieurs jours et plages (1, 5, 7-12, 21, par exemple).  
  
 **Une fois**  
 Définit une planification qui s'exécute une seule fois. Utilisez la section **Dates de début et de fin** pour spécifier le jour d'exécution de la planification. La planification expire dès qu'elle a été traitée.  
  
 **Dates de début et de fin**  
 Spécifie une date de début qui détermine à quel moment la planification prend effet et une date de fin qui détermine à quel moment la planification expire. Les planifications expirent sans notification. Après la date de fin, une planification ne s'exécute plus.  
  
## <a name="saving-the-subscription"></a>Enregistrement de l'abonnement  
 Le bouton **Terminer** est activé lorsqu'il existe suffisamment d'informations pour l'abonnement. Cliquez sur **Terminer** pour terminer l'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
