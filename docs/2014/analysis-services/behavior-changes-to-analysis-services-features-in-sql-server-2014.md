---
title: Changements de comportement pour Analysis Services des fonctionnalités dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0f7cc154a79a329bc18d02535e3f3332aa7e8b61
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62655840"
---
# <a name="behavior-changes-to-analysis-services-features-in-sql-server-2014"></a>Modifications de comportement des fonctionnalités Analysis Services dans SQL Server 2014
  Cette rubrique décrit les modifications de comportement dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour les déploiements Multidimensionnel, Tabulaire, Exploration de données et [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] . Les modifications de comportement affectent le mode de fonctionnement ou d’interaction des fonctionnalités dans la version actuelle de SQL Server par rapport aux versions précédentes.  
  
> [!NOTE]  
>  En revanche, une modification avec rupture empêche un modèle de données ou une application intégrée à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de s’exécuter. Pour en savoir plus, consultez [Modifications avec rupture dans les fonctionnalités Analysis Services de SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md).  
  
 Dans cette rubrique :  
  
-   [Changements de comportement dans SQL Server 2014](#bkmk_sql2014)  
  
-   [Changements de comportement dans SQL Server 2012 SP1](#bkmk_sql2012sp1)  
  
-   [Changements de comportement dans SQL Server 2012](#bkmk_sql2012)  
  
##  <a name="bkmk_sql2014"></a> Changements de comportement dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Les fonctionnalités des modes Tabulaire, Multidimensionnel, Exploration de données ou [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] de cette version ne font l’objet d’aucune nouvelle modification de comportement.  Toutefois, compte tenu de la forte similitude entre  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] et les versions [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] , les modifications de comportement des deux versions précédentes sont fournies ici à titre informatif au cas où votre mise à niveau porterait sur [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
##  <a name="bkmk_sql2012sp1"></a> Changements de comportement dans [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]  
 Cette section documente les modifications de comportement signalées pour les fonctionnalités de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Ces modifications s’appliquent également à [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
|Problème|Description|  
|-----------|-----------------|  
|Les classeurs PowerPivot SQL Server 2008 R2 ne mettent pas à niveau et n'actualisent pas silencieusement les modèles lorsqu'ils sont utilisés dans SQL Server 2012 SP1 PowerPivot pour SharePoint 2013. Par conséquent, les actualisations de données planifiée ne fonctionnent pas pour les classeurs PowerPivot SQL Server 2008 R2.|Les classeurs SQL Server 2008 R2 s’ouvrent dans [!INCLUDE[ssGeminiShortvnext](../includes/ssgeminishortvnext-md.md)], mais les actualisations planifiées ne fonctionnent pas. Si vous observez l'historique d'actualisation, vous pouvez voir un message d'erreur semblable au message suivant :<br /> « Le classeur contient un modèle PowerPivot non pris en charge. Le modèle PowerPivot dans le classeur est au format SQL Server 2008 R2 PowerPivot pour Excel 2010. Les modèles PowerPivot pris en charge sont les suivants : <br />SQL Server 2012 PowerPivot pour Excel 2010<br />SQL Server 2012 PowerPivot pour Excel 2013 »<br /><br /> **La mise à niveau un classeur :** L’actualisation planifiée ne fonctionne pas jusqu'à ce que vous mettez à niveau le classeur vers un classeur 2012. Pour mettre à niveau le classeur et le modèle qu'il contient, procédez de l'une des façons suivantes :<br /><br /> Téléchargez et ouvrez le classeur dans Microsoft Excel 2010 avec le complément SQL Server 2012 PowerPivot pour Excel installé. Ensuite, enregistrez le classeur et republiez-le sur le serveur SharePoint.<br /><br /> Téléchargez et ouvrez le classeur dans Microsoft Excel 2013. Ensuite, enregistrez le classeur et republiez-le sur le serveur SharePoint.<br /><br /> <br /><br /> Pour plus d’informations sur la mise à niveau du classeur, consultez [mettre les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).|  
|Modification du comportement dans la [ALL Function](https://msdn.microsoft.com/library/ee634802(v=sql.120).aspx)DAX|Avant [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)], si vous spécifiez une colonne [Date] dans Marquer en tant que table de dates, en vue d'une utilisation dans Time Intelligence, et la colonne [Date] est passée en tant qu'argument à la fonction ALL, qui à sont tour, est passée en tant que filtre à une fonction CALCULATE, tous les filtres de toutes les colonnes de la table sont ignorés, quel que soit le segment de la colonne de dates.<br /><br /> Par exemple,<br /><br /> `= CALCULATE (<expression>, ALL (DateTable[Date]))`<br /><br /> Avant [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)], tous les filtres sont ignorés pour toutes les colonnes de DateTable, quel que soit la colonne [Date] passée en tant qu'argument à la fonction ALL.<br /><br /> Dans [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] et dans PowerPivot dans Excel 2013, les filtres ne sont ignorés que pour la colonne spécifiée passée en tant qu'argument à la fonction ALL.<br /><br /> Pour contourner le nouveau comportement, ignorer toutes les colonnes passées en tant que filtre pour l'intégralité de la table, excluez la colonne [Date] de l'argument, par exemple.<br /><br /> `=CALCULATE (<expression>, ALL(DateTable))`<br /><br /> Le résultat obtenu sera identique à celui du comportement antérieur à [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].|  
  
##  <a name="bkmk_sql2012"></a> Changements de comportement dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Cette section documente les changements de comportement signalés pour les fonctionnalités de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Ces modifications s’appliquent également à [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
### <a name="analysis-services-multidimensional-mode"></a>Analysis Services, mode multidimensionnel  
  
#### <a name="nullprocessing-option-set-to-preserve-is-no-longer-supported-for-distinct-count-measures"></a>L’option NullProcessing avec la valeur Preserve n’est plus prise en charge pour les mesures de comptage de valeurs  
 Antérieures à [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], il était possible de définir [NullProcessing élément &#40;ASSL&#41; ](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl) à `Preserve` pour les mesures de comptage.  Malheureusement, cette pratique entraînait souvent des résultats non valides, voire dans certains cas le blocage du travail de traitement. Cette configuration n’est donc plus valide dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Toute tentative d’utilisation il entraîne l’erreur de validation suivante se produise : « Erreurs dans le Gestionnaire de métadonnées. Preserve n’est pas une valeur NullProcessing valide pour le \<measurename > mesure de comptage de valeurs. »  
  
#### <a name="cube-browser-in-management-studio-and-cube-designer-has-been-removed"></a>L'explorateur de cube dans Management Studio et le Concepteur de cube a été supprimé  
 Le contrôle explorateur de cube qui vous permet d'effectuer un glisser-déplacer des champs sur une structure de tableau croisé dynamique dans Management Studio ou le Concepteur de cube a été supprimé du produit. Le contrôle était un composant OWC (Office Web Control). OWC a été déconseillé par Office et n'est plus disponible.  
  
### <a name="powerpivot-for-sharepoint"></a>PowerPivot pour SharePoint  
  
#### <a name="higher-permission-requirements-for-using-a-powerpivot-workbook-as-an-external-data-source"></a>Autorisation d'un niveau supérieur requise pour l'utilisation d'un classeur PowerPivot comme source de données externe  
 Un classeur Excel peut restituer des données PowerPivot incorporées dans le même classeur ou dans un classeur externe. Dans la version précédente, les spécifications relatives aux autorisations étaient les mêmes, que les données PowerPivot soient incorporées ou externes. Si vous aviez des autorisations **Vue seule** sur un classeur PowerPivot, vous pouviez obtenir un accès complet à toutes les données PowerPivot du classeur pour les connexions incorporées et externes.  
  
 Dans cette version, les spécifications relatives aux autorisations ont changé pour les classeurs Excel qui restituent des données PowerPivot à partir d'un fichier externe. Dans cette version, vous devez avoir des autorisations **Lire** (ou plus spécifiquement, l'autorisation **Ouvrir les éléments** ) pour vous connecter à un classeur PowerPivot externe à partir d'une application cliente. Des autorisations supplémentaires spécifient qu'un utilisateur dispose de droits de téléchargement pour consulter les données sources incorporées dans le classeur. Les autorisations supplémentaires reflètent le fait que les données de modèle sont entièrement accessibles par l'application cliente ou le classeur lié à celle-ci, avec pour résultat un meilleur alignement entre les spécifications d'autorisation et le comportement réel de connexion des données.  
  
 Pour continuer à utiliser un classeur PowerPivot comme source de données externe, vous devez élargir les autorisations SharePoint des utilisateurs qui se connectent aux données PowerPivot externes. Jusqu'à ce que vous modifiiez les autorisations, les utilisateurs obtiennent l’erreur suivante s’ils tentent d’accéder à des classeurs PowerPivot dans une connexion de source de données : « Le service PowerPivot Web a retourné une erreur (accès refusé. Le document que vous avez demandée n’existe pas ou vous n’êtes pas autorisé à ouvrir le fichier.) »  
  
> [!WARNING]  
>  Les étapes suivantes expliquent comment arrêter l'héritage des autorisation au niveau de la bibliothèque et changer les autorisations des utilisateurs de **Vue seule** à **Lire** pour les documents spécifiques de cette bibliothèque. Avant de continuer, examinez attentivement les autorisations existantes et les documents et vérifiez que ces étapes sont appropriées pour votre site.  
>   
>  Vous pouvez également créer un dossier dans la bibliothèque, y déplacer tous les documents affectés et attribuer des autorisations uniques sur le dossier.  
  
> [!NOTE]  
>  Si vos classeurs sont stockés dans la Galerie PowerPivot, l'arrêt de l'héritage des autorisations interrompra la génération d'images miniatures pour ce classeur s'il est configuré pour l'actualisation des données. Pour autoriser simultanément l'accès aux classeurs et aux images d'aperçu dans la galerie, accordez des autorisations **Lire** à des utilisateurs spécifiques au niveau de bibliothèque, pour tous les documents dans la bibliothèque.  
  
 Vous devez être le propriétaire du site pour modifier des autorisations.  
  
 **Comment élargir des autorisations au niveau lecture pour des classeurs individuels**  
  
1.  Cliquez sur la flèche du bas pour ouvrir le menu d'un document individuel.  
  
2.  Cliquez sur **Gérer les autorisations**.  
  
3.  Par défaut, une bibliothèque hérite les autorisations. Pour modifier les autorisations des classeurs individuels dans cette bibliothèque, cliquez sur **Arrêter l’héritage des autorisations**.  
  
4.  Sélectionnez la case à cocher pour les utilisateur ou les groupes qui requièrent des autorisations supplémentaires sur les classeurs PowerPivot. Les autorisations supplémentaires permettront à ces utilisateurs d'accéder aux données PowerPivot incorporées et de les utiliser comme source de données externe dans d'autres documents.  
  
5.  Cliquez sur **Modifier les autorisations des utilisateurs**.  
  
6.  Choisissez les autorisations de **Lecture** , puis cliquez sur **OK**.  
  
#### <a name="powerpivot-gallery-new-rules-for-snapshot-generation-for-some-powerpivot-workbooks"></a>Galerie PowerPivot : Nouvelles règles pour la génération d’instantanés pour certains classeurs PowerPivot  
 Cette version prévoit une nouvelle configuration requise pour la génération d'images d'instantané dans la Galerie PowerPivot et élimine la source d'une potentielle divulgation d'informations (à savoir, afficher un instantané de données d'une source de données que vous n'avez pas l'autorisation d'afficher). Cette configuration s'applique uniquement aux classeurs PowerPivot qui se connectent aux sources de données externes chaque fois que vous les consultez. Si vous utilisez uniquement des classeurs qui visualisent les données PowerPivot incorporées, vous ne constaterez aucun changement de comportement pour la génération d'instantanés dans la Galerie PowerPivot.  
  
 Pour un classeur qui actualise ses données chaque fois qu'il s'ouvre, la nouvelle configuration requise pour la génération d'instantanés est la suivante :  
  
-   Les classeurs PowerPivot utilisés comme sources de données externes par les autres classeurs ou rapports doivent être dans la même bibliothèque que les classeurs qui consomment les données. Par exemple, si vous avez un classeur sales-data.xlsx qui fournit des données au classeur sales-report.xlsx, les deux classeurs doivent être dans la galerie pour que les images d'instantané s'affichent.  
  
-   Les classeurs utilisés ensemble doivent hériter des autorisations d'un parent commun (autrement dit, la Galerie PowerPivot). Dans notre exemple, les classeurs sales-data.xlsx et sales-report.xlsx doivent hériter de la Galerie PowerPivot.  
  
 Si un classeur ne correspond pas aux critères ci-dessus, l'icône verrouillée suivante apparaîtra au lieu de l'image miniature que vous attendez :  
  
 ![GMNI_PowerPivotGalleryIcon_Locked](media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")  
  
#### <a name="new-default-setting-for-load-balancing-requests-changed-from-round-robin-to-health-based"></a>Le nouveau paramètre par défaut pour les demandes d'équilibrage de la charge a été modifié de Tourniquet (round robin) à Selon l'intégrité  
 Une application de service PowerPivot possède des paramètres par défaut qui déterminent la façon dont les demandes de données PowerPivot sont réparties entre plusieurs serveurs PowerPivot pour SharePoint dans une batterie. Dans la version précédente, le paramètre par défaut était **Tourniquet (round robin)** et les demandes étaient distribuées séquentiellement entre les serveurs disponibles. Dans cette version, la valeur par défaut est **Selon l'intégrité.** L'application de service PowerPivot utilise des statistiques d'intégrité du serveur, telles que la mémoire ou l'UC disponible, pour déterminer quelle instance de serveur obtient la demande xt.  
  
 Si vous avez mis à niveau votre serveur à partir de la version précédente, l'application de service PowerPivot conserve le paramètre par défaut précédent (**Tourniquet (round robin)**). Pour utiliser le paramètre de la méthode d'allocation **Selon l'intégrité** , vous devez modifier les paramètres de configuration. Pour plus d’informations, consultez [Créer et configurer une application de service PowerPivot](power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)   
 [Modifications avec rupture Analysis Services des fonctionnalités dans SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)  
  
  
