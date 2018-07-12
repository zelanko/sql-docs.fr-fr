---
title: Configurer la collecte de données d’utilisation pour (PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 955ca6d6-9d5b-47a4-a87c-59bd23f1bf74
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 06dfd95c82aab8e3fed336863c75112728150247
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149751"
---
# <a name="configure-usage-data-collection-for-powerpivot-for-sharepoint"></a>Configurer la collecte des données d'utilisation (PowerPivot pour SharePoint)
  La collecte des données d'utilisation est une fonctionnalité SharePoint au niveau de la batterie de serveurs. Le service PowerPivot pour SharePoint utilise et étend ce système pour fournir des rapports intégrés dans le tableau de bord de gestion PowerPivot qui indiquent la manière dont les données et services PowerPivot sont utilisés. Selon la façon dont vous avez installé votre serveur SharePoint, la collecte des données d'utilisation peut être désactivée pour la batterie de serveurs. Un administrateur de batterie doit activer la journalisation de l'utilisation pour créer les données d'utilisation qui s'affichent dans le tableau de bord de gestion PowerPivot.  
  
 Pour plus d’informations sur les données d’utilisation dans le tableau de bord de gestion PowerPivot, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **Dans cette rubrique :**  
  
 [Activer la collecte des données d'utilisation et choisir les événements qui déclenchent la collecte des données](#events)  
  
 [Définir l'emplacement du fichier journal](#configdb)  
  
 [Configurer les travaux du minuteur utilisés dans la collecte des données d'utilisation](#jobs)  
  
 [Limiter la durée de conservation de l'historique des données d'utilisation](#confighist)  
  
 [Définir des catégories de temps de réponse aux requêtes lents, moyens et rapides à des fins de création de rapports](#qrh)  
  
 [Spécifier la fréquence à laquelle les statistiques sur les requêtes sont consignées dans le système de collecte des données d'utilisation](#ttr)  
  
 [Ouvrez la page d’Application de Service PowerPivot pour accéder aux paramètres de configuration](#openconfig)  
  
 [La configuration par défaut pour la collecte de données d’utilisation PowerPivot](#defaultconfig)  
  
> [!IMPORTANT]  
>  Les données d'utilisation fournissent des indications sur la manière dont les utilisateurs accèdent aux données et aux ressources, mais elles ne permettent pas de bénéficier de données permanentes et fiables sur les opérations serveur et l'accès de l'utilisateur. Par exemple, en cas de redémarrage d'un serveur, les données d'utilisation de l'événement sont perdues et ne peuvent pas être récupérées. De même, si la taille maximale des fichiers journaux temporaires a été atteinte, aucune nouvelle donnée n'est ajoutée tant que les fichiers n'ont pas été effacés. Si vous avez besoin de fonctionnalités d'audit, vous pouvez utiliser les fonctions de type de contenu et de flux de travail de SharePoint pour générer un sous-système d'audit pour votre batterie. Plus d'informations, essayez d'obtenir la documentation du produit et des informations de la communauté sur le Web.  
  
##  <a name="events"></a> Activer la collecte des données d'utilisation et choisir les événements qui déclenchent la collecte des données  
 Configurez la collecte des données d'utilisation dans l'Administration centrale de SharePoint.  
  
1.  Dans l'Administration centrale, cliquez sur **Analyse**.  
  
2.  Dans la section **Création de rapports**, cliquez sur **Configurer la collecte des données d'utilisation et d'intégrité**.  
  
3.  Sélectionnez **Activer la collecte des données d'utilisation**.  
  
4.  Dans la section **Événements à enregistrer** , activez ou désactivez les cases à cocher afin d'activer ou de désactiver les événements Analysis Services suivants :  
  
    |Événement|Description|  
    |-----------|-----------------|  
    |**Connexions PowerPivot**|L'événement de connexion PowerPivot permet de superviser les connexions serveur PowerPivot établies pour le compte d'un utilisateur.|  
    |**Utilisation des données de chargement PowerPivot**|L'utilisation des données de chargement PowerPivot permet de superviser les demandes qui chargent des données PowerPivot dans la mémoire du serveur. Un événement de chargement est généré pour les fichiers de données PowerPivot chargées à partir d'une base de données de contenu ou du cache.|  
    |**Utilisation des données de déchargement PowerPivot**|L'utilisation des données de déchargement PowerPivot permet de superviser les demandes de déchargement pour une source de données PowerPivot après une période d'inactivité. La mise en cache d'une source de données PowerPivot sur le disque est signalée comme un événement de déchargement.|  
    |**Utilisation des requêtes PowerPivot**|Utilisation des requêtes PowerPivot permet de superviser les temps de traitement des requêtes pour les données chargées dans un [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance.|  
  
    > [!NOTE]  
    >  Les opérations d'actualisation des données et d'intégrité des serveurs génèrent également des données d'utilisation, mais aucun événement n'est associé à ces processus.  
  
5.  Vous pouvez également mettre à jour l'emplacement du fichier journal. Pour plus d'informations, consultez la section suivante.  
  
6.  Cliquez sur **OK** pour enregistrer vos modifications.  
  
7.  Vous pouvez éventuellement spécifier si tous les messages sont journalisés, ou uniquement les erreurs. Pour plus d’informations sur la limitation des messages d’événements, consultez [configurer et afficher les fichiers journaux SharePoint et la journalisation des diagnostics &#40;PowerPivot pour SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md).  
  
##  <a name="configdb"></a> Définir l'emplacement du fichier journal  
 Les données d'utilisation PowerPivot sont stockées initialement dans les fichiers journaux d'utilisation sur le serveur local, puis déplacées régulièrement vers les bases de données d'application de service PowerPivot. L'emplacement du fichier journal est défini dans l'Administration centrale. L'emplacement par défaut est :  
  
 `C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\logs`  
  
 Pour afficher ou modifier ces propriétés, utilisez la page **Collection des données d'utilisation et d'intégrité** .  
  
1.  Sur la page d'accueil de l'Administration centrale, cliquez sur **Analyse**.  
  
2.  Dans la section Supervision, cliquez sur **Configurer la collecte des données d'utilisation et d'intégrité**.  
  
3.  Dans Paramètres de collecte des données d'utilisation, affichez ou modifiez l'emplacement, le nom ou la taille maximale du fichier. Si vous spécifiez une taille de fichier trop faible, la limite maximale sera atteinte et aucune entrée ne sera ajoutée au fichier tant que son contenu n'aura pas été déplacé vers la base de données centrale de collecte des données d'utilisation.  
  
##  <a name="jobs"></a> Configurer les travaux du minuteur utilisés dans la collecte des données d'utilisation  
 Les données d'intégrité et d'utilisation du serveur PowerPivot sont déplacées vers divers emplacements du système de collecte des données d'utilisation à l'aide de deux travaux du minuteur :  
  
-   Le travail du minuteur « Importation des données d'utilisation de Microsoft SharePoint Foundation » déplace les données d'utilisation PowerPivot vers la base de données d'application de service PowerPivot.  
  
-   Le travail du minuteur pour le traitement du tableau de bord de gestion des données PowerPivot déplace les données vers un classeur PowerPivot qui est la source des données des rapports d'administration intégrés.  
  
 Si vous devez actualiser plus fréquemment les rapports d'administration qui s'affichent dans le tableau de bord de gestion PowerPivot, suivez ces étapes.  
  
1.  Dans l'Administration centrale, cliquez sur **Analyse**.  
  
2.  Cliquez sur **Examiner les définitions de travail** Dans la section **Travaux du minuteur** .  
  
3.  Cliquez sur **Importation des données d'utilisation de Microsoft SharePoint Foundation**.  
  
4.  Cliquez sur **Exécuter maintenant**. Si le bouton **Exécuter maintenant** est désactivé, cliquez sur **Activer** , puis cliquez sur **Exécuter maintenant**.  
  
5.  Dans la liste Définitions de travaux, cliquez sur **Travail du minuteur pour le traitement du tableau de bord de gestion des données PowerPivot**.  
  
6.  Cliquez sur **Exécuter maintenant**.  
  
7.  Vérifiez les rapports pour consulter les données d'actualisation. Pour plus d’informations, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
##  <a name="confighist"></a> Limiter la durée de conservation de l'historique des données d'utilisation  
 L'historique des données d'utilisation est stocké pour les événements (connexions, chargement, déchargement et traitement des requêtes à la demande) et l'actualisation des données (traitement des données planifié). Bien que les données d'utilisation soient collectées via le système de collecte des données d'utilisation de SharePoint, les données de création de rapports sont déplacées vers une base de données d'application PowerPivot et une base de données de création de rapports pour le stockage à plus long terme. L'historique des données d'utilisation détermine la durée de conservation des données d'utilisation dans les bases de données d'application PowerPivot. La même limite est appliquée systématiquement à tous les types de données d'utilisation stockées dans la même base de données d'application de service PowerPivot.  
  
1.  [Ouvrez la page Application de service PowerPivot](#openconfig).  
  
2.  Dans la section **Collecte des données d'utilisation** , sous **Historique des données d'utilisation**, entrez le nombre de jours pendant lequel vous souhaitez conserver un enregistrement de l'activité d'actualisation des données pour chaque classeur.  
  
    -   La valeur par défaut est 365 jours.  
  
    -   La valeur 0 spécifie une durée de stockage illimitée : les données d'utilisation sont conservées indéfiniment.  
  
    -   Si vous le souhaitez, vous pouvez spécifier une plage comprise entre 1 et 5 000 jours.  
  
     La définition d'une durée de rétention moins importante entraînera la suppression de toutes les données qui dépassent la nouvelle limite. Par exemple, si vous remplacez la valeur 365 par la valeur 30, les données d'utilisation seront supprimées pour toutes les données historiques qui se sont produites il y a plus de 30 jours. Seules les données concernant les 30 derniers jours seront conservées.  
  
     Les données sont supprimées lorsque l'événement suivant se produit. La limite de l'historique des données d'utilisation est vérifiée uniquement lorsque le système traite un événement.  
  
3.  Cliquez sur **OK**.  
  
 Pour plus d’informations sur comment les données d’utilisation sont collectées et stockées, consultez [PowerPivot Usage Data Collection](power-pivot-usage-data-collection.md).  
  
##  <a name="qrh"></a> Définir des catégories de temps de réponse aux requêtes lents, moyens et rapides à des fins de création de rapports  
 Les performances de traitement des requêtes sont mesurées par rapport à des catégories prédéfinies qui définissent un cycle de requête-réponse en fonction de sa durée d'exécution. Les catégories prédéfinies sont les suivantes : Triviale, Rapide, Attendue, Longue et Hors limite. Chaque demande auprès d'un serveur PowerPivot appartient à l'une des catégories en fonction de sa durée d'exécution.  
  
 Les informations de réponse à une requête sont utilisées dans les rapports d'activité. Dans les rapports, chaque catégorie est utilisée différemment pour révéler de manière plus efficace les tendances des performances du système PowerPivot. Par exemple, les demandes triviales sont totalement exclues, car leur exclusion supprime le bruit dans les données et affiche des tendances plus significatives avec les catégories restantes. Par opposition, les statistiques sur les demandes longues ou hors limite sont les plus importantes dans le rapport afin que les administrateurs ou les propriétaires de classeurs puissent entreprendre l'action corrective sur le champ.  
  
 Bien que vous ne puissiez pas ajouter ou supprimer des catégories, vous pouvez définir les limites supérieure et inférieure qui déterminent la fin d'une catégorie et le début de la suivante. Si votre organisation utilise des contrats de niveau de service (SLA) pour définir les niveaux acceptables de performances et de disponibilité des serveurs, vous pouvez adapter ces catégories pour qu'elles reflètent le contrat SLA que vous créez.  
  
1.  [Ouvrez la page Application de service PowerPivot](#openconfig).  
  
2.  Dans la section **Collecte des données d'utilisation** , sous **Limite supérieure de réponse triviale** , entrez une valeur (en millisecondes) qui définit la limite supérieure d'exécution d'une réponse triviale. En général, les demandes faisant partie de cette catégorie sont les suivantes : requête ping de serveur, initiation de session et requête de métadonnées. La valeur par défaut est 500 millisecondes (une demi-seconde).  
  
3.  Dans Limite supérieure des demandes rapides, entrez une valeur (en millisecondes) qui définit la limite supérieure pour l'exécution d'une réponse rapide. Les demandes faisant partie de cette catégorie sont les suivantes : requêtes de datasets très petits ou serveurs de métadonnées de datasets importants. La valeur par défaut est 1 000 millisecondes (une seconde).  
  
4.  Dans la section **Limite supérieure de réponse attendue**, entrez une valeur (en millisecondes) définissant la limite supérieure pour l’exécution d’une réponse dans un laps de temps moyen ou attendu. Les demandes qui font partie de cette catégorie incluent le chargement de données dans une visionneuse. La valeur par défaut est 3 000 millisecondes (trois secondes).  
  
5.  Dans la section **Limite supérieure de réponse longue**, entrez une valeur (en millisecondes) définissant la limite supérieure pour l’exécution d’une réponse longue. Les demandes faisant partie de cette catégorie ont une durée d'exécution plus longue que prévue, qui reste cependant dans une plage acceptable. La valeur par défaut est 10 000 millisecondes (dix secondes).  
  
     Les requêtes qui dépassent cette limite sont classées comme étant *Hors limite*. Il n'existe pas de seuil configurable pour *Hors limite*. Ce seuil est déduit de la limite supérieure que vous spécifiez pour Limite supérieure des demandes longues. Les requêtes appartenant à la catégorie Hors limite ont une durée d'exécution plus longue que celle autorisée par un contrat SLA que vous avez défini.  
  
6.  Cliquez sur **OK**.  
  
##  <a name="ttr"></a> Spécifier la fréquence à laquelle les statistiques sur les requêtes sont consignées dans le système de collecte des données d'utilisation  
 L'intervalle de création de rapports de requête spécifie la fréquence de consignation des statistiques sur les requêtes dans le système de collecte des données d'utilisation. Les statistiques sur les requêtes s'accumulent dans un processus et sont consignées, sous la forme d'un événement, à intervalles réguliers. Vous pouvez modifier la fréquence afin que les statistiques soient écrites dans le fichier journal selon une fréquence plus ou moins élevée.  
  
1.  [Ouvrez la page Application de service PowerPivot](#openconfig).  
  
2.  Dans la section **Collecte des données d'utilisation** , sous **Intervalle de création de rapports de requête**, entrez le nombre de secondes au terme duquel le serveur consignera les statistiques sur les requêtes pour toutes les catégories (triviale, rapide, attendue, longue et hors limite) sous la forme d'un événement dans le système de collecte des données d'utilisation.  
  
    -   La plage valide est comprise entre 1 et n'importe quel entier positif.  
  
    -   La valeur par défaut est 300 secondes (cinq minutes). Cette valeur est recommandée pour les environnements de batterie de serveurs dynamiques qui exécutent divers services et applications.  
  
     Si vous définissez un nombre beaucoup plus élevé, vous risquez de perdre des données statistiques avant qu'elles ne soient consignées. Par exemple, le redémarrage d'un service entraînera la perte des statistiques sur les requêtes. Inversement, si vos rapports d'activité intégrés affichent des données insuffisantes, vous pouvez diminuer la fréquence pour obtenir plus souvent des événements d'intervalle de création de rapports.  
  
3.  Cliquez sur **OK**.  
  
##  <a name="openconfig"></a> Ouvrez la page d’Application de Service PowerPivot pour accéder aux paramètres de configuration  
 Vous devez être administrateur de batterie de serveurs ou de services pour pouvoir modifier les paramètres d'applications de service. Si vous avez défini plusieurs applications de service PowerPivot dans la batterie de serveurs, vous devez les modifier une à une.  
  
1.  Dans l'Administration centrale de SharePoint, dans **Gestion des applications**, cliquez sur **Gérer les applications de service**.  
  
2.  Recherchez l'application de service PowerPivot. Vous pouvez reconnaître une application de service à son type. Un type d'application de service PowerPivot est **Application de service PowerPivot**.  
  
3.  Cliquez sur le nom de l'application de service PowerPivot. Le tableau de bord de gestion PowerPivot s'ouvre.  
  
4.  Dans **Actions**, cliquez sur **Configurer les paramètres d'application de service**. La page Paramètres d'application de service PowerPivot s'ouvre.  
  
##  <a name="defaultconfig"></a> La configuration par défaut pour la collecte de données d’utilisation PowerPivot  
 La collecte des données d'utilisation pour les opérations de service PowerPivot peut être activée avec les paramètres par défaut afin qu'elle soit disponible immédiatement dans les applications qui prennent en charge la fonctionnalité d'intégration Analysis Services. Les paramètres par défaut sont les événements qui déclenchent la collecte des données d'utilisation, les limites de durée de stockage des données d'utilisation et les seuils pour le classement des temps de réponse aux requêtes.  
  
 Le tableau suivant affiche les valeurs par défaut pour la configuration de la collecte des données d'utilisation.  
  
|Paramètre|Valeur par défaut|Type|Plage valide|  
|-------------|-------------------|----------|-----------------|  
|**Événements d’utilisation Analysis Services** (connexion, chargement, déchargement, requêtes)|\<activé >|Booléen|Ces valeurs sont activées ou désactivées.|  
|**Query Reporting interval**|300 (en secondes)|Entier|Comprise entre 1 et n'importe quel entier positif. La valeur par défaut est 5 minutes.|  
|**Usage data history**|365 (en jours)|Entier|La valeur 0 spécifie une durée illimitée, mais vous pouvez également définir une limite supérieure pour l'expiration des données d'historique qui sont alors automatiquement supprimées. Les valeurs valides pour une période de rétention limitée sont comprises entre 1 et 5 000 (en jours).|  
|Limite supérieure de réponse triviale|500 (en millisecondes)|Entier|Définit une limite maximale qui définit un échange requête-réponse triviale. Toute demande dont la durée d'exécution est comprise entre 0 et 500 millisecondes est une demande triviale ; elle est ignorée à des fins de création de rapports.|  
|Limite supérieure de réponse rapide|1000 (en millisecondes)|Entier|Définit une limite maximale qui définit un échange requête-réponse rapide.|  
|Limite supérieure de réponse attendue|3000 (en millisecondes)|Entier|Définit une limite maximale qui définit un échange requête-réponse attendue.|  
|Limite supérieure de réponse longue|10 000 (en millisecondes)|Entier|Définit une limite maximale qui définit un échange requête-réponse long. Toute demande qui dépasse cette limite est classée dans la catégorie Hors limite pour laquelle il n'existe pas de seuil maximal.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de paramètre de configuration &#40;PowerPivot pour SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Collecte des données d’utilisation de PowerPivot](power-pivot-usage-data-collection.md)  
  
  
