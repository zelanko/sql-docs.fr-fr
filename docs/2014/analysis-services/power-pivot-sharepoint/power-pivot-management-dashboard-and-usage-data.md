---
title: Tableau de bord de gestion PowerPivot et données d’utilisation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ece3d8a1e9a66ecc6ad05508c975e617c523a9c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071119"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a>Tableau de bord de gestion PowerPivot et données d'utilisation
  Le tableau de bord de gestion PowerPivot est une collection de rapports et de composants WebPart prédéfinis dans l'Administration centrale de SharePoint, qui vous aident à administrer un déploiement de SQL Server PowerPivot pour SharePoint. Le tableau de bord de gestion fournit des informations sur l'intégrité du serveur, l'activité du classeur et l'actualisation des données. Le tableau de bord utilise les données issues de la collecte des données d'utilisation de SharePoint.  
  
 [Prérequis](#prereq)  
  
 [Vue d’ensemble des sections du tableau de bord](#items)  
  
 [Ouvrir le Tableau de bord de gestion PowerPivot](#open)  
  
 [Données sources dans les tableaux de bord](#sourcedata)  
  
 [Modifier le tableau de bord PowerPivot](#edit)  
  
 [Créer des rapports personnalisés pour le Tableau de bord de gestion PowerPivot](#reports)  
  
##  <a name="prereq"></a>Conditions préalables  
 Pour ouvrir le tableau de bord de gestion PowerPivot pour une application de service PowerPivot que vous gérez, vous devez être administrateur du service.  
  
##  <a name="items"></a>Vue d’ensemble des sections du tableau de bord  
 Le tableau de bord de gestion PowerPivot contient des composants WebPart et des rapports incorporés qui explorent des catégories d'informations spécifiques. La liste suivante décrit chaque élément du tableau de bord :  
  
|tableau de bord|Description|  
|---------------|-----------------|  
|Infrastructure - Intégrité du serveur|Affiche les tendances d'utilisation de l'UC, de consommation de mémoire et de temps de réponse aux requêtes au fil du temps afin que vous puissiez évaluer si les ressources système s'approchent de leur capacité maximale ou sont sous-utilisées.|  
|Actions|Contient des liens vers d'autres pages de l'Administration centrale, notamment l'application de service actuelle, une liste des applications de service et la journalisation de l'utilisation.|  
|Activité du classeur - Graphique|Crée des rapports sur la fréquence des accès aux données. Vous pouvez connaître le nombre de connexions aux sources des données PowerPivot établies chaque jour ou chaque semaine.|  
|Activité du classeur - Liste|Crée des rapports sur la fréquence des accès aux données. Vous pouvez connaître le nombre de connexions aux sources des données PowerPivot établies chaque jour ou chaque semaine.|  
|Actualisation des données - Activité récente|Crée des rapports sur l'état des travaux d'actualisation des données, y compris ceux dont l'exécution a échoué. Ce rapport fournit un affichage composite des opérations d'actualisation des données au niveau de l'application. Les administrateurs peuvent d'un coup d'œil voir le nombre de travaux d'actualisation des données définis pour l'application de service PowerPivot dans son intégralité.|  
|Actualisation des données - Défaillances récentes|Répertorie les classeurs PowerPivot pour lesquels l'actualisation des données n'a pas abouti.|  
|Rapports|Contient des liens vers des rapports que vous pouvez ouvrir dans Excel.|  
  
##  <a name="open"></a>Ouvrir le tableau de bord de gestion PowerPivot  
 Le tableau de bord affiche les informations d'une seule application de service PowerPivot à la fois. Vous pouvez ouvrir le tableau de bord de gestion à partir de deux emplacements.  
  
### <a name="open-the-dashboard-from-general-application-settings"></a>Ouvrir le tableau de bord à partir des Paramètres généraux de l'application  
  
1.  Dans l'Administration centrale, dans le groupe **Paramètres généraux de l'application** , cliquez sur **Tableau de bord de gestion PowerPivot**.  
  
2.  Dans la page principale, sélectionnez l'application de service PowerPivot dont vous souhaitez consulter les données opérationnelles.  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a>Ouvrir le tableau de bord à partir d'une application de service PowerPivot  
  
1.  Dans administration centrale, dans **gestion des applications**, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur le nom de l'application de service PowerPivot. Le tableau de bord de gestion PowerPivot affiche les données opérationnelles de l'application de service actuelle.  
  
### <a name="change-the-current-service-application"></a>Modifiez l'application de service actuelle.  
 Pour modifier l'application de service PowerPivot actuelle dans le tableau de bord de gestion :  
  
1.  En haut du tableau de bord de gestion PowerPivot, notez le nom de l’application de service actuelle, par exemple **application de service PowerPivot par défaut**.  
  
2.  Dans le tableau de bord **Actions** , cliquez sur **Lister les applications de service**.  
  
3.  Cliquez sur le nom de l'application de service PowerPivot dont vous souhaitez afficher les rapports du tableau de bord de gestion.  
  
##  <a name="sourcedata"></a>Données sources dans les tableaux de bord  
 Les tableaux de bord, rapports et composants WebPart affichent les données à partir d'un modèle de données interne qui extrait des données du système et des bases de données d'application PowerPivot. Le modèle de données interne est incorporé dans un classeur PowerPivot hébergé sur le site Administration centrale. La structure du modèle de données est fixe. Même si vous pouvez utiliser le classeur PowerPivot comme source de données pour créer des rapports, vous ne devez pas en modifier la structure d'une manière qui risquerait de rompre les rapports prédéfinis qui l'utilisent.  
  
 Pour plus d'informations sur la procédure de collecte des données, consultez les rubriques suivantes :  
  
-   [Collecte des données d'utilisation PowerPivot](power-pivot-usage-data-collection.md)  
  
-   [Configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 Pour capturer des données sur le système du serveur PowerPivot, vérifiez que la messagerie d'événements, l'historique d'actualisation des données et les autres historiques d'utilisation sont activés pour chaque application de service PowerPivot. Les données sur le serveur et l'utilisation collectées lors du fonctionnement normal du serveur constituent la source de données utilisée dans le modèle de données interne. **Remarque :** Si vous désactivez l’historique des événements ou de l’utilisation, les rapports composites seront incomplets ou erronés.  
  
##  <a name="edit"></a>Modifier le tableau de bord PowerPivot  
 Si vous avez des compétences en matière de développement ou de personnalisation de tableaux de bord, vous pouvez modifier le tableau de bord pour y inclure de nouveaux composants WebPart. Vous avez également la possibilité de modifier les propriétés des composants WebPart inclus dans le tableau de bord.  
  
##  <a name="reports"></a>Créer des rapports personnalisés pour le tableau de bord de gestion PowerPivot  
 À des fins de création de rapports, les données d'utilisation et l'historique PowerPivot sont conservés dans un classeur PowerPivot interne créé et configuré en même temps que le tableau de bord. Si les rapports par défaut ne fournissent pas les informations qui vous intéressent, vous pouvez créer des rapports personnalisés dans Excel, basés sur le classeur. Le classeur et tous les rapports personnalisés créés sont conservés si vous mettez à niveau ou désinstallez les fichiers solution PowerPivot ultérieurement. Le classeur et les rapports sont stockés dans la bibliothèque de gestion PowerPivot sur le site Administration centrale. Cette bibliothèque n'est pas visible par défaut, mais vous pouvez l'afficher en utilisant l'action Afficher tout le contenu du site dans les Actions du site.  
  
 Pour vous aider à prendre en main la génération de rapports personnalisés, le tableau de bord de gestion PowerPivot propose un fichier Office Data Connection (.odc) pour la connexion au classeur source. Par exemple, vous pouvez utiliser le fichier .odc dans Excel pour créer des rapports supplémentaires.  
  
> [!NOTE]  
>  Modifiez le fichier pour éviter l'erreur suivante lors de la tentative d'utilisation du fichier .odc dans Excel : « Échec de l'initialisation de la source de données ». Le fichier .odc généré automatiquement inclut un paramètre qui n'est pas pris en charge par le fournisseur OLE DB MSOLAP. Les instructions suivantes fournissent la solution de contournement permettant de supprimer ces paramètres.  
  
 Vous devez être administrateur de batterie de serveurs ou de service pour générer des rapports basés sur le classeur PowerPivot dans l'Administration centrale.  
  
1.  Ouvrez le Tableau de bord de gestion PowerPivot.  
  
2.  Accédez à la section **Rapports** , au bas de la page.  
  
3.  Cliquez sur **Données de gestion PowerPivot**.  
  
4.  Enregistrez le fichier .odc dans un dossier local.  
  
5.  Ouvrez le fichier .odc dans un éditeur de texte.  
  
6.  Dans l'élément `<odc:ConnectionString>`, allez jusqu'à la fin de la ligne et supprimez `Embedded Data=False`, puis supprimez `Edit Mode=0`. Si le dernier caractère de la chaîne est un point-virgule, supprimez-le.  
  
7.  Enregistrez le fichier. Les étapes restantes dépendent de la version de PowerPivot et d'Excel que vous utilisez.  
  
8.  1.  Démarrez Excel 2013  
  
    2.  Dans le ruban **PowerPivot** , cliquez sur **Gérer**.  
  
    3.  Cliquez sur **Données externes** puis sur **Connexions existantes**.  
  
    4.  Cliquez sur le fichier .ODC si vous le voyez. Si vous ne voyez pas le fichier .ODC, cliquez sur **Parcourir** , puis dans le chemin d'accès du fichier, spécifiez le fichier .odc.  
  
    5.  Cliquez sur **ouvrir**  
  
    6.  Cliquez sur **Tester la connexion** pour vérifier que la connexion aboutit.  
  
    7.  Entrez un nom pour la connexion, puis cliquez sur **Suivant**.  
  
    8.  Dans spécifier la requête MDX, cliquez sur **conception** pour ouvrir le concepteur de requêtes MDX afin d’assembler les données que vous souhaitez utiliser **si vous voyez le message d’erreur** « le nom de la propriété du mode d’édition n’est pas mis en forme correctement. », vérifiez que vous modifiez le. Fichier ODC.  
  
    9. Cliquez sur **OK** , puis sur **Terminer**.  
  
    10. Créez des rapports de tableau croisé dynamique ou de graphique croisé dynamique pour visualiser les données dans Excel.  
  
9. 1.  Démarrez Excel 2010.  
  
    2.  Sur le ruban PowerPivot, cliquez sur **Lancer Fenêtre PowerPivot**.  
  
    3.  Sur le ruban Conception de la fenêtre PowerPivot, cliquez sur **Connexions existantes**.  
  
    4.  Cliquez sur **Parcourir**.  
  
    5.  Dans le chemin d'accès, spécifiez le fichier .odc.  
  
    6.  Cliquez sur **Ouvrir**. L'Assistant Importation de table démarre, à l'aide de la chaîne de connexion au classeur PowerPivot qui contient les données d'utilisation.  
  
    7.  Cliquez sur **Tester la connexion** pour vérifier l'accès.  
  
    8.  Entrez un nom convivial pour la connexion, puis cliquez sur **Suivant**.  
  
    9. Dans Spécifier la requête MDX, cliquez sur **Conception** pour ouvrir le concepteur de requêtes MDX afin d'assembler les données avec lesquelles vous souhaitez travailler, puis créez des rapports de tableau croisé dynamique ou de graphique croisé dynamique pour visualiser les données dans Excel.  
  
## <a name="see-also"></a>Voir aussi  
 [Actualisation des données PowerPivot avec SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
