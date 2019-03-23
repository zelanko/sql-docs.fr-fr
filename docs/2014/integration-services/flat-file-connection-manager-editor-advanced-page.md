---
title: Éditeur du Gestionnaire de connexions de fichier (Page avancé) plats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columnproperties.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 58aa3dee-4774-4e0b-a956-96d199be4c3a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 067bb5a2da9a93bc29e93a3844a29e1a4028c7d0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58380467"
---
# <a name="flat-file-connection-manager-editor-advanced-page"></a>Éditeur du gestionnaire de connexions de fichiers plats (page Avancé)
  La page **Avancé** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** vous permet de définir des propriétés qui spécifient la manière dont Integration Services lit et écrit des données dans les fichiers plats. Vous pouvez modifier les noms des colonnes dans le fichier plat et définir des propriétés qui incluent le type de données et des séparateurs pour chaque colonne du fichier.  
  
 Par défaut, la longueur des colonnes de type chaîne est de 50 caractères. Vous pouvez redimensionner la longueur de ces colonnes pour empêcher la troncation des données ou une largeur de colonne excessive. Vous pouvez également mettre à jour d'autres métadonnées pour permettre la compatibilité avec les colonnes de destination. Par exemple, vous pouvez convertir le type de données d'une colonne qui contient uniquement des données de type entier en type de données numérique, tel que DT_I2. Vous pouvez apporter ces modifications manuellement ou cliquer sur le bouton **Sélectionner les types** pour utiliser la boîte de dialogue **Suggérer les types de colonnes** pour évaluer des échantillons de données et effectuer automatiquement une partie de ces modifications.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats, consultez [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Nom du gestionnaire de connexions**  
 Spécifiez un nom unique pour le gestionnaire de connexions de fichiers plats dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Configurez les propriétés de chaque colonne**  
 Dans le volet gauche, sélectionnez une colonne pour afficher ses propriétés dans celui de droite. Le tableau ci-dessous fournit une description des définitions des types de données. Certaines de ces propriétés peuvent uniquement être configurées pour certains formats de fichiers plats.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**ColumnType**|Indique si la colonne est délimitée, si elle a une largeur fixe ou si elle présente un format en drapeau à droite. Cette propriété est en lecture seule. Les fichiers en drapeau à droite sont des fichiers dans lesquels chaque colonne a une largeur fixe, à l'exception de la dernière colonne. Un séparateur de lignes s'applique.|  
|**OutputColumnWidth**|Indiquez une valeur spécifiant la largeur de colonne en nombre d'octets. Pour les fichiers Unicode, cette valeur correspond à un nombre de caractères. Dans la tâche de flux de données, cette valeur permet de définir la largeur de la colonne de sortie pour les fichiers plats sources.<br /><br /> Remarque : Dans le modèle objet, le nom de la propriété est MaximumWidth.|  
|**DataType**|Sélectionnez un type de données dans la liste des types de données disponibles. Pour plus d'informations, consultez [Integration Services Data Types](data-flow/integration-services-data-types.md).|  
|**TextQualified**|Indique si les données de texte sont entourées par des caractères de qualificateur de texte tels que des caractères de guillemets. Les valeurs valides sont :<br /><br /> **True**: Les données texte du fichier plat sont qualifiées.<br /><br /> **False**: Les données texte du fichier plat ne sont pas qualifiées.|  
|**Nom**|Précisez un nom de colonne descriptif. Si vous n'entrez aucun nom, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] crée automatiquement un nom au format Colonne 0, Colonne 1, et ainsi de suite.|  
|**DataScale**|Spécifiez l'échelle des données numériques. L'échelle est le nombre de décimales. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Sélectionnez un délimiteur de colonnes dans la liste des séparateurs de colonnes disponibles. Veillez à choisir un caractère de séparation qu'il est peu probable de rencontrer dans le texte. Cette valeur est ignorée dans le cas des colonnes à largeur fixe.<br /><br /> **{CR}{LF}**. Les colonnes sont délimitées par une combinaison retour chariot-saut de ligne.<br /><br /> **{CR}**. Les colonnes sont séparées par un retour chariot.<br /><br /> **{LF}**. Les colonnes sont séparées par un saut de ligne.<br /><br /> **Point-virgule {;}**. Les colonnes sont séparées par un point-virgule.<br /><br /> **Deux-points {:}**. Les colonnes sont séparées par un deux-points.<br /><br /> **Virgule {,}**. Les colonnes sont séparées par une virgule.<br /><br /> **Tabulation {t}**. Les colonnes sont séparées par une tabulation.<br /><br /> **Barre verticale {&#124;}**. Les colonnes sont séparées par une barre verticale.|  
|**DataPrecision**|Spécifiez la précision des données numériques. La précision indique le nombre total de chiffres. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).|  
|**InputColumnWidth**|Indiquez une valeur spécifiant la largeur de colonne en nombre d'octets. Pour les fichiers Unicode, cette valeur est exprimée en nombre de caractères. Cette valeur est ignorée dans le cas des colonnes délimitées.<br /><br /> **Remarque** : Dans le modèle objet, le nom de cette propriété est ColumnWidth.|  
  
 **Nouveau**  
 Ajoutez une nouvelle colonne en cliquant sur **Nouveau**. Par défaut, ce **nouveau** bouton ajoute une nouvelle colonne à la fin de la liste. Le bouton possède également les options ci-dessous, disponibles dans la liste déroulante.  
  
|Value|Description|  
|-----------|-----------------|  
|**Ajouter une colonne**|Ajoute une colonne à la fin de la liste.|  
|**Insérer avant**|Insère une nouvelle colonne avant la colonne sélectionnée.|  
|**Insérer après**|Insère une nouvelle colonne après la colonne sélectionnée.|  
  
 **Supprimer**  
 Sélectionnez une colonne, puis supprimez-la en cliquant sur **Supprimer**.  
  
 **Suggérer les types**  
 La boîte de dialogue **Suggérer les types de colonnes** permet d’évaluer des échantillons de données dans le fichier et d’obtenir des suggestions pour le type de données et la longueur de chaque colonne. Pour plus d’informations, consultez [Référence de l’interface utilisateur de la boîte de dialogue Suggérer les types de colonnes](connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
