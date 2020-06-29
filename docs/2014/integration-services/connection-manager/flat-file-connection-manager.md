---
title: Gestionnaire de connexions de fichiers plats | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], Flat File
- connections [Integration Services], flat files
- files [Integration Services], connections
- Flat File connection manager
- flat files
- flat file connections [Integration Services]
ms.assetid: 7830f80d-af32-4e8f-a6fc-f03af6bc1946
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55d44369a0d6d57f876bb08475266955c87724b1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438466"
---
# <a name="flat-file-connection-manager"></a>Gestionnaire de connexions de fichiers plats
  Un gestionnaire de connexions de fichiers plats permet à un package d'accéder aux données d'un fichier plat. Ainsi, les sources et destinations de fichiers plats peuvent utiliser des gestionnaires de connexions de fichiers plats pour extraire et charger des données.  
  
 Le gestionnaire de connexions de fichiers plats peut accéder à un seul fichier. Pour référencer plusieurs fichiers, utilisez un gestionnaire de connexions de fichiers plats multiples plutôt qu'un gestionnaire de connexions de fichiers plats. Pour plus d’informations, consultez [Gestionnaire de connexion de fichiers plats multiples](multiple-flat-files-connection-manager.md).  
  
## <a name="column-length"></a>Longueur de colonne  
 Par défaut, le gestionnaire de connexions de fichiers plats définit la longueur des colonnes de chaînes à 50 caractères. Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** , vous pouvez évaluer les exemples de données et redimensionner automatiquement la longueur de ces colonnes pour empêcher la troncation de données ou une largeur de colonnes excessive. En outre, sauf si vous redimensionnez ultérieurement la longueur de colonne dans une source de fichiers plats ou une transformation, la longueur de colonne de la colonne de chaîne reste la même dans tout le flux de données. Si ces colonnes de chaînes sont mappées à des colonnes de destination plus étroites, des avertissements apparaissent dans l'interface utilisateur. En outre, au moment de l'exécution, des erreurs peuvent se produire en raison de la troncation des données. Pour éviter les erreurs ou la troncation, vous pouvez redimensionner les colonnes pour assurer leur compatibilité avec les colonnes de destination dans le gestionnaire de connexions de fichiers plats, la source de fichiers plats ou une transformation. Pour modifier la longueur des colonnes de sortie, définissez la `Length` propriété de la colonne de sortie sous l’onglet **propriétés d’entrée et de sortie** de la boîte de dialogue **éditeur avancé** .  
  
 Si vous mettez à jour les longueurs de colonnes dans le gestionnaire de connexions de fichiers plats après l'ajout et la configuration de la source de fichiers plats qui utilise le gestionnaire de connexions, il n'est pas nécessaire de redimensionner manuellement les colonnes de sortie dans la source de fichiers plats. Quand vous ouvrez la boîte de dialogue **Source du fichier plat** , la source du fichier plat offre la possibilité de synchroniser les métadonnées de la colonne.  
  
## <a name="configuration-of-the-flat-file-connection-manager"></a>Configuration du gestionnaire de connexions de fichiers plats  
 Lorsque vous ajoutez un gestionnaire de connexions de fichiers plats à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera résolu en une connexion de fichier plat au moment de l’exécution, définit les propriétés de connexion de fichier plat et ajoute le gestionnaire de connexions de fichiers plats à la `Connections` collection du package.  
  
 La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `FLATFILE`.  
  
 Par défaut, le gestionnaire de connexions de fichiers plats cherche toujours la présence d'un séparateur de lignes dans les données non délimitées par des guillemets, puis démarre une nouvelle ligne lorsqu'un séparateur de lignes est trouvé. Cela permet au gestionnaire de connexions de fichiers plats d'analyser correctement les fichiers comportant des lignes auxquelles il manque des champs de colonnes.  
  
 Dans certains cas, la désactivation de cette fonctionnalité peut améliorer les performances des packages. Vous pouvez désactiver cette fonctionnalité en définissant la propriété du gestionnaire de connexions de fichiers plats, **alwayscheckforrowdelimiters du**, sur `False` .  
  
 Vous pouvez configurer le gestionnaire de connexions de fichiers plats de plusieurs manières :  
  
-   Spécifiez le fichier, les paramètres régionaux et la page de codes à utiliser. Les paramètres régionaux sont utilisés pour interpréter les données spécifiques à un pays comme les dates, tandis que la page de codes est utilisée pour convertir les données chaînes au format Unicode.  
  
-   Spécifiez le format de fichier. Vous pouvez utiliser un format délimité, à largeur fixe ou en drapeau à droite.  
  
-   Spécifiez une ligne d'en-tête, une ligne de données et des séparateurs de colonnes. Les séparateurs de colonnes peuvent être définis au niveau du fichier et remplacés au niveau de la colonne.  
  
-   Indiquez si la première ligne du fichier contient les noms de colonnes.  
  
-   Spécifiez un caractère d'identificateur de texte. Chaque colonne peut être configurée pour reconnaître un identificateur de texte.  
  
     L'utilisation d'un caractère qualificateur pour incorporer un caractère qualificateur dans une chaîne qualifiée est désormais prise en charge. La double instance d'un qualificateur de texte est interprétée comme une instance littérale et unique de cette chaîne. Par exemple, si l’identificateur de texte est un guillemet simple et si les données d’entrée sont 'abc', 'def', 'g'hi', les données de sortie sont abc, def, g'hi.  
  
-   Définissez des propriétés comme le nom, le type de données et la largeur maximale pour des colonnes individuelles.  
  
 Vous pouvez définir la propriété ConnectionString du gestionnaire de connexions de fichiers plats en spécifiant une expression dans la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour éviter une erreur de validation, procédez comme suit.  
  
-   Quand vous utilisez une expression pour spécifier le fichier, ajoutez un chemin de fichier dans la zone **Nom du fichier** de **l’Éditeur du gestionnaire de connexions de fichiers plats**.  
  
-   Attribuez à la propriété **DelayValidation** du gestionnaire de connexions de fichiers plats la valeur **True**.  
  
 Vous pouvez utiliser une expression pour créer un nom de fichier au moment de l'exécution à l'aide du gestionnaire de connexions de fichiers plats, avec la destination du fichier plat.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../flat-file-connection-manager-editor-columns-page.md)  
  
-   [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../flat-file-connection-manager-editor-advanced-page.md)  
  
-   [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../flat-file-connection-manager-editor-preview-page.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  
