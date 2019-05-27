---
title: Définir la compatibilité de niveau d’une base de données multidimensionnelle (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c5eedfb396b33d33ceb9fbfad0245c4eb730997
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66076687"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a>Définir le niveau de compatibilité d'une base de données multidimensionnelle (Analysis Services)
  Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], la propriété du niveau de compatibilité de la base de données détermine le niveau fonctionnel d'une base de données. Les niveaux de compatibilité sont propres à chaque type de modèle. Par exemple, un niveau de compatibilité de `1100` a une signification différente selon que la base de données est multidimensionnelle ou tabulaire.  
  
 Cette rubrique décrit le niveau de compatibilité des bases de données multidimensionnelles uniquement. Pour plus d’informations sur les solutions tabulaires, consultez [niveau de compatibilité &#40;SSAS tabulaire SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
> [!NOTE]  
>  Les modèles tabulaires possèdent des niveaux de compatibilité de base de données qui ne s'appliquent pas aux modèles multidimensionnels. Le niveau de compatibilité `1103` n'existe pas pour les modèles multidimensionnels. Consultez [quelles sont les nouveautés du modèle tabulaire dans le niveau de compatibilité et de SQL Server 2012 SP1](https://go.microsoft.com/fwlink/?LinkId=301727) pour plus d’informations sur `1103` pour les solutions tabulaires.  
  
 **Niveaux de compatibilité des bases de données multidimensionnelles**  
  
 Actuellement, le seul comportement de base de données multidimensionnelle qui varie selon le niveau de compatibilité est l'architecture de stockage de chaînes. En augmentant le niveau de compatibilité d'une base de données, vous pouvez dépasser la limite de 4 Go pour le stockage de chaînes de mesures et de dimensions.  
  
 Pour une base de données multidimensionnelle, les valeurs valides pour la propriété `CompatibilityLevel` sont les suivantes :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|`1050`|Cette valeur n'est pas visible dans un script ou des outils, mais elle correspond aux bases de données créées dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Toute base de données pour laquelle `CompatibilityLevel` n'est pas défini explicitement, s'exécute implicitement au niveau `1050`.|  
|`1100`|C'est la valeur par défaut pour les nouvelles bases de données que vous créez dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Vous pouvez également la spécifier pour les bases de données créées dans les versions antérieures de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour permettre l'utilisation des fonctionnalités prises en charge uniquement à ce niveau de compatibilité (à savoir, le stockage amélioré des chaînes pour les attributs de dimension ou les mesures de comptage des valeurs qui contiennent les données de chaîne).<br /><br /> Bases de données qui ont un `CompatibilityLevel` définie sur `1100` comportent une propriété supplémentaire, `StringStoresCompatibilityLevel`, qui vous permet de choisir les autre stockage de chaînes pour les partitions et dimensions.|  
  
> [!WARNING]  
>  La définition de la compatibilité de la base de données sur un niveau supérieur est irrévocable. Après avoir augmenté le niveau de compatibilité à `1100`, vous devez continuer à exécuter la base de données sur les serveurs plus récents. Vous ne pouvez pas restaurer à `1050`. Vous ne pouvez pas attacher ni restaurer une `1100` base de données sur une version de serveur antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Les niveaux de compatibilité de la base de données ont été introduits dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Vous devez disposer de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou ultérieur pour visualiser ou définir le niveau de compatibilité de la base de données.  
  
 La base de données ne peut pas être un cube local. Les cubes locaux ne prennent pas en charge la propriété `CompatibilityLevel`.  
  
 La base de données doit avoir été créée dans une version précédente (SQL Server 2008 R2 ou antérieure), puis attachée ou restaurée sur un serveur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou plus récent. Les bases de données déployées vers SQL Server 2012 sont déjà au niveau `1100` et ne peuvent pas être déclassifiées pour s'exécuter à un niveau inférieur.  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a>Déterminer le niveau de compatibilité de la base de données existant pour une base de données multidimensionnelle  
 La seule façon d'afficher ou modifier le niveau de compatibilité de la base de données est de passer par XMLA. Vous pouvez afficher ou modifier le script XMLA qui spécifie la base de données dans SQL Server Management Studio.  
  
 Si vous recherchez la définition XMLA d'une base de données pour la propriété `CompatibilityLevel` et qu'elle 'existe pas, vous disposez probablement d'une base de données au niveau de compatibilité `1050`.  
  
 Vous trouverez des instructions pour l'affichage et la modification du script XMLA dans la section suivante.  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a>Définir le niveau de compatibilité de la base de données dans SQL Server Management Studio  
  
1.  Avant d'augmenter le niveau de compatibilité, sauvegardez la base de données au cas où vous souhaiteriez annuler les modifications apportées.  
  
2.  Connectez-vous au serveur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui héberge la base de données à l’aide de SQL Server Management Studio.  
  
3.  Cliquez avec le bouton droit sur le nom de la base de données, pointez sur **Générer un script de la base de données en tant que**, sur **ALTER To**, puis sélectionnez **Nouvelle fenêtre d’éditeur de requête**. Une représentation XMLA de la base de données s'ouvre dans une nouvelle fenêtre.  
  
4.  Copiez l'élément XML suivant :  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  Collez-le après l'élément de fin `</Annotations>` et avant l'élément `<Language>` . Le XML doit ressembler à l'exemple suivant :  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  Enregistrez le fichier.  
  
7.  Pour exécuter le script, cliquez sur **Exécuter** dans le menu Requête ou appuyez sur F5.  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a>Opérations prises en charge qui requièrent le même niveau de compatibilité  
 Les opérations suivantes requièrent que les bases de données sources partagent le même niveau de compatibilité.  
  
1.  La fusion de partitions de bases de données différentes est prise en charge uniquement si les deux bases de données partagent le même niveau de compatibilité.  
  
2.  L'utilisation de dimensions liées d'une autre base de données requiert le même niveau de compatibilité. Par exemple, si vous souhaitez utiliser une dimension liée d’une [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] dans la base de données un [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] base de données, vous devez déplacer le [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] de base de données à un [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] server et définir la compatibilité de niveau sur `1100`.  
  
3.  La synchronisation des serveurs est prise en charge uniquement pour les serveurs qui partagent la même version et le même niveau de compatibilité de base de données.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir augmenté le niveau de compatibilité de la base de données, vous pouvez définir la propriété `StringStoresCompatibilityLevel` dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Cela augmente le stockage des chaînes de mesures et de dimensions. Pour plus d’informations sur cette fonctionnalité, consultez [Configurer le stockage de chaînes pour des dimensions et des partitions](configure-string-storage-for-dimensions-and-partitions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
