---
title: "Mettre à niveau Analysis Services | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
caps.latest.revision: 79
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3b3ad4ecf62f3a30882720140f2f362007f8428b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="upgrade-analysis-services"></a>Mettre à niveau Analysis Services
  Les instances d’Analysis Services peuvent être mises à niveau vers une version SQL Server du même mode de serveur pour tirer parti des fonctionnalités introduites dans la version actuelle, comme décrit dans [Nouveautés d’Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md).  
  
 Vous pouvez mettre à niveau chaque instance sur place, indépendamment des autres instances exécutées sur le même matériel. Toutefois, la plupart des administrateurs choisissent d’installer une nouvelle instance de la nouvelle version pour tester l’application avant de transférer les charges de travail de production vers le nouveau serveur. Une mise à niveau sur place peut cependant être plus adaptée pour les serveurs de développement ou de test.  
  
 Avant de mettre à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez les rubriques suivantes :  

- [Notes de publication de SQL Server 2017](../../sql-server/sql-server-2017-release-notes.md) décrit les problèmes connus et les solutions de contournement.  
- [Notes de publication de SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) décrit les problèmes connus et les solutions de contournement.  
- [Analysis Services Backward Compatibility](../../analysis-services/analysis-services-backward-compatibility.md) répertorie les fonctionnalités supprimées, déconseillées et modifiées. Pensez à consulter ces listes régulièrement pour évaluer l’impact des modifications apportées au produit sur vos modèles, scripts ou code personnalisé. En général, les transitions de fonctionnalités sont annoncées dans la version préliminaire de la prochaine version majeure.  
  
## <a name="server-upgrade"></a>Mise à niveau du serveur  
 Il existe deux approches de base pour mettre à niveau les serveurs et les bases de données :  
  
-   Une**mise à niveau sur place** remplace les fichiers programme existants par les fichiers programme de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Les bases de données restent au même emplacement. Les dossiers programme sont mis à jour pour refléter le nouveau nom.  
  
-   Une**mise à niveau côte à côte** crée une nouvelle installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], généralement sur le même ordinateur, sauf si vous mettez à niveau le matériel en même temps. Dans cette approche, vous devez déplacer les bases de données vers la nouvelle instance, puis éventuellement désinstaller la version précédente pour libérer de l’espace disque.  
  
 Les niveaux de compatibilité des bases de données attachées à un serveur donné restent inchangés, sauf si vous les modifiez manuellement.  
  
### <a name="in-place-upgrade"></a>Mise à niveau sur place  
 Vous pouvez mettre à niveau une instance existante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et, dans le cadre du processus de mise à niveau, migrer automatiquement les bases de données existantes de l'instance précédente vers la nouvelle. Comme les métadonnées et les données binaires sont compatibles entre les deux versions, vous conserverez les données après la mise à niveau et vous n'avez pas à migrer les données manuellement.  
  
 Pour mettre à niveau une instance existante, exécutez le programme d'installation et spécifiez le nom de l'instance existante comme nom de la nouvelle instance.  
  
### <a name="side-by-side-upgrade"></a>Mise à niveau côte à côte  
  
-   Sauvegardez toutes les bases de données et vérifiez que chacune d’elles peut être restaurée. Consultez [Backup and Restore of Analysis Services Databases](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
-   Identifiez un sous-ensemble de rapports, de feuilles de calcul ou d’instantanés de tableaux de bord à utiliser plus tard comme base pour confirmer les opérations de serveur après la mise à niveau. Si possible, collectez les mesures de performances pour pouvoir effectuer des comparaisons avec les mêmes charges de travail sur un serveur mis à niveau.  
  
-   Installez une nouvelle instance d’Analysis Services en choisissant le même mode de serveur (tabulaire ou multidimensionnel) que le serveur à remplacer. Consultez [Install Analysis Services](../../analysis-services/instances/install-windows/install-analysis-services.md).  
  
     Suivez les tâches consécutives à l’installation pour configurer les ports et ajouter des administrateurs de serveur. Consultez [Configuration consécutive à l’installation &#40;Analysis Services&#41;](../../analysis-services/instances/post-install-configuration-analysis-services.md).  
  
-   Attachez ou restaurez chaque base de données.  
  
-   Exécutez DBCC pour vérifier l’intégrité des bases de données. Les modèles tabulaires sont soumis à une vérification plus approfondie, avec des tests pour les objets orphelins dans l’ensemble de la hiérarchie du modèle. Pour les modèles multidimensionnels, seuls les index de partition sont vérifiés. Consultez [DBCC &#40;Database Consistency Checker&#41; pour les bases de données multidimensionnelles et tabulaires Analysis Services](../../analysis-services/instances/database-consistency-checker-dbcc-for-analysis-services.md).  
  
-   Testez les rapports, feuilles de calcul et tableaux de bord pour vérifier que le comportement ou les calculs n’ont subi aucune modification indésirable. Vous devriez constater une amélioration des performances pour les charges de travail multidimensionnelles et tabulaires.  
  
-   Testez les opérations de traitement et corrigez les éventuels problèmes de connexion ou d’autorisation. Si vous utilisez un compte de service par défaut pour les connexions, le nouveau service s’exécute sous un compte différent. Consultez [Configurer les comptes de service &#40;Analysis Services&#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md) pour plus d’informations sur les comptes de démarrage pour Analysis Services.  
  
-   Testez les opérations de sauvegarde et de restauration sur le serveur mis à niveau, en modifiant les scripts pour qu’ils utilisent le nom du nouveau serveur.  
  
## <a name="database-upgrade"></a>Mise à niveau des bases de données  
 Les bases de données créées dans les versions antérieures d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécutent sur le serveur mis à niveau sous un ancien paramétrage de niveau de compatibilité de base de données. En général, vous pouvez mettre à niveau une base de données ou un modèle pour améliorer son niveau de compatibilité afin d’accéder à de nouvelles fonctionnalités, mais sachez que cela vous oblige à utiliser une version spécifique du serveur.  
  
 En général, pour mettre à niveau une base de données, vous mettez à niveau le modèle dans SQL Server Data Tools (SSDT), puis déployez la solution vers une instance de serveur mise à niveau. Consultez la page [Télécharger SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx) pour obtenir la version la plus récente.  
  
 Les bases de données tabulaires et multidimensionnelles suivent des chemins d’accès de version différents. Le fait que les modèles multidimensionnels et tabulaires aient tous deux un niveau de compatibilité de 1100 est une coïncidence.  Les modes avancent à des vitesses différentes si les modifications de fonctionnalités n’affectent que l’un d’eux.  
  
 Le tableau suivant présente simplement les niveaux de compatibilité. Nous vous recommandons toutefois de consulter les rubriques détaillées pour savoir ce que fournit chaque niveau.  
  
||||  
|-|-|-|  
|Tabulaire|1200|SQL Server 2016|  
|Tabulaire|1103|SQL Server 2014|  
|Tabulaire|1100|SQL Server 2012|  
|(Multidimensionnel)|1100|SQL Server 2012 et versions ultérieures|  
|(Multidimensionnel)|1050|SQL Server 2005, 2008, 2008 R2|  
  
 Pour plus d’informations, consultez [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md) et [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
## <a name="tabular-model-upgrade-to-1200-compatibility-level"></a>Mise à niveau du modèle tabulaire vers le niveau de compatibilité 1200  
 Les bases de données et modèles tabulaires tirent le meilleur parti de SQL Server 2016. Cette version propose un mode DirectQuery révisé pour les modèles tabulaires au niveau de compatibilité 1200, simplifié par la suppression du mode hybride, l’ajout d’instructions de requête pour récupérer un sous-ensemble de données au moment de la conception, et la sécurité au niveau des lignes via DAX au lieu des autorisations de ligne dans la base de données principale.  
  
 La nouvelle construction de métadonnées tabulaires au sein du modèle offre une deuxième raison de mettre à niveau. Un modèle tabulaire au niveau de compatibilité 1200, créé ou élevé à ce niveau, utilise une terminologie native pour les définitions d’objets (tels que modèle, table, relations et colonnes) pour décrire ses principaux éléments.  
  
 Pour mettre à niveau un modèle tabulaire, utilisez une version de [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx) conçue pour cette version de façon à remplacer la valeur de la propriété **CompatibilityLevel** par **SQL Server 2016 RTM (1200)**.  
  
 N’utilisez pas SSMS, de code ou de script pour modifier **CompatibilityLevel**. Le remplacement de la propriété en soi n’a aucune incidence. La conversion de métadonnées se produit dans SSDT en réponse à la mise à jour de la propriété, suivie de la réouverture du projet.  
  
 Comme toujours, pensez à enregistrer une sauvegarde de votre modèle avant de mettre à niveau au cas où vous deviez revenir à la version précédente.  
  
1.  Dans SSDT > Explorateur de solutions, cliquez avec le bouton droit sur **model.bim**, choisissez **Afficher le code**, puis vérifiez que le modèle sera bien fermé puis rouvert dans une nouvelle fenêtre (la fenêtre de code).  
  
2.  Le modèle s’ouvre sous forme de document XMLA. À des fins de comparaison post-conversion, copiez le contenu dans un autre fichier (vous pouvez ouvrir un nouveau fichier XML dans SSDT).  
  
3.  Cliquez avec le bouton droit sur **model.bim** et redéfinissez-le sur **Concepteur de vues**.  
  
4.  Définissez **CompatibilityLevel** sur  **SQL Server 2016 RTM (1200)**.  
  
5.  Cette étape ne pouvant pas être annulée, vous êtes invité à confirmer l’action. Pour continuer, cliquez sur **Oui** . Le projet va être actualisé.  
  
6.  Cliquez avec le bouton droit sur **model.bim** et redéfinissez-le sur **Afficher le code**.  
  
     Notez que la définition du modèle est désormais au format JSON, avec des métadonnées tabulaires.  
  
 **Conversion de métadonnées**  
  
 En comparant les métadonnées avant et après conversion, vous constatez que celles-ci sont converties au format JSON et débarrassées des définitions redondantes.  
  
 Le modèle conserve toutes ses fonctionnalités : les liaisons de données, secteurs de partition, expressions, identificateurs d’objet, noms d’objet, descriptions, légendes, traductions et annotations restent intacts. Cependant, si un code ou un script fait référence à des objets spécifiques, une partie de la réécriture du code sera consacrée à la suppression des références aux objets qui n’existent plus. Par exemple, un modèle 1050 ou 1103 comportera des sections pour les dimensions externes au cube, tandis qu’un modèle 1200 définit une table comme un objet unique.  
  
> [!NOTE]  
>  Les anciens niveaux de compatibilité tabulaire de 1050 et 1103 sont pris en charge, mais déconseillés. Dans une version ultérieure de SQL Server, les modèles tabulaires considérés comme des objets multidimensionnels ne seront plus pris en charge. Consultez [Deprecated Analysis Services Features in SQL Server 2016](../../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md) pour lire l’annonce.  
  
## <a name="post-upgrade-for-tabular-models-at-1200-compatibilitylevel"></a>Version après mise à niveau pour les modèles tabulaires au niveau de compatibilité 1200  
 Après avoir converti le modèle, vous rédigerez le script des opérations de base de données avec le [langage de script de modèle tabulaire &#40;TMSL&#41;](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) et non XMLA. TMSL est généré automatiquement dans SSMS lorsque le modèle est 1200. Le code personnalisé qui cible les bases de données tabulaires 1200 doit utiliser l’API définie dans l’espace de noms Microsoft.AnalysisServces.Tabular. Le script et le code doivent être écrits de toutes pièces. Il n’existe aucun mécanisme de conversion intégrée. Aidez-vous du [guide du développeur (Analysis Services)](../../analysis-services/analysis-services-developer-documentation.md) pour vous faciliter la prise en main.  
  
 Vous pouvez également ajouter les fonctionnalités suivantes à un modèle tabulaire, prises en charge uniquement au niveau de compatibilité 1200 :  
  
-   Une implémentation DirectQuery qui prend en charge la sécurité au niveau des lignes via DAX dans le modèle, davantage de sources de données, des sous-ensembles de données à des fins de modélisation et une configuration simplifiée.  
  
-   Colonnes calculées  
  
-   Dossiers d’affichage  
  
## <a name="upgrade-tabular-models-in-directquery-mode"></a>Mettre à niveau des modèles tabulaires en mode DirectQuery  
 Vous ne pouvez pas effectuer une mise à niveau sur place des anciens modèles tabulaires configurés pour DirectQuery. La nouvelle implémentation de DirectQuery exige une configuration moindre et tous les paramètres ne peuvent pas être déplacés.  
  
1.  Dans SSDT, désactivez le mode **DirectQuery** pour que le modèle utilise le stockage en mémoire. Consultez [Activer le mode Création DirectQuery (SSAS Tabulaire)](https://msdn.microsoft.com/library/hh270245.aspx) pour obtenir des instructions.  
  
2.  Définissez **CompatibilityLevel** sur SQL Server 2016 (RTM) 1200.  
  
3.  Enregistrez et régénérez ou déployez le modèle.  
  
4.  Réactivez **DirectQuery** . Pour obtenir des instructions, consultez [DirectQuery for Tabular 1200 models](http://msdn.microsoft.com/library/4227977e-7368-4d45-b78f-24076882e7a8) .  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Nouveautés d’Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Planification d’une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Mettre à niveau Power Pivot pour SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Installer Analysis Services en mode multidimensionnel et exploration de données](http://msdn.microsoft.com/library/8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60)   
 [Effectuer une mise à niveau vers SQL Server 2016 à l’aide de l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  

