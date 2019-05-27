---
title: Éditeur du Gestionnaire de connexions (Page avancé) de fichiers plats multiples | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multifile.advanced.f1
helpviewer_keywords:
- Multiple Flat Files Connection Manager Editor
ms.assetid: fc883131-c03d-4ab3-8220-b51cbe243a82
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: de238c1012a255ceb59086e542d5529b8b907915
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66057546"
---
# <a name="multiple-flat-files-connection-manager-editor-advanced-page"></a>Éditeur du gestionnaire de connexions de fichiers plats multiples (page Avancé)
  Utilisez la page **Avancé** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats multiples** pour définir des propriétés comme le type de données et les délimiteurs de chaque colonne des fichiers texte auxquels le gestionnaire de connexions de fichiers plats se connecte.  
  
 Par défaut, la longueur des colonnes de type chaîne est de 50 caractères. Vous pouvez évaluer des exemples de données et redimensionner automatiquement la longueur de ces colonnes pour empêcher la troncation des données ou une largeur de colonne excessive. Vous pouvez également mettre à jour d'autres métadonnées pour permettre la compatibilité avec les colonnes de destination. Par exemple, vous pouvez convertir le type de données d'une colonne qui contient uniquement des données de type entier en type de données numérique, tel que DT_I2.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats multiples, consultez [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Nom du gestionnaire de connexions**  
 Fournissez un nom unique pour le gestionnaire de connexions de fichiers plats multiples dans le flux de travail. Le nom fourni sera affiché dans la zone **Gestionnaires de connexion** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Configurez les propriétés de chaque colonne**  
 Dans le volet gauche, sélectionnez une colonne pour afficher ses propriétés dans celui de droite. Le tableau ci-dessous fournit une description des définitions des types de données. Certaines de ces propriétés peuvent uniquement être configurées pour certains formats de fichiers plats.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**ColumnType**|Indique si la colonne est délimitée, si elle a une largeur fixe ou si elle présente un format en drapeau à droite. Cette propriété est en lecture seule. Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est arrêtée par le séparateur de lignes.|  
|**OutputColumnWidth**|Indiquez une valeur spécifiant la largeur de colonne en nombre d'octets. Pour les fichiers Unicode, cette valeur est exprimée en nombre de caractères. Dans la tâche de flux de données, cette valeur permet de définir la largeur de la colonne de sortie pour les fichiers plats sources.<br /><br /> Remarque : Dans le modèle objet, le nom de la propriété est MaximumWidth.|  
|**DataType**|Sélectionnez un type de données dans la liste des types de données disponibles. Pour plus d'informations, consultez [Integration Services Data Types](data-flow/integration-services-data-types.md).|  
|**TextQualified**|Indiquez si les données texte sont qualifiées à l'aide d'un caractère identificateur de texte. Les valeurs valides sont :<br /><br /> **True** : Données de texte dans le fichier plat sont qualifiées.<br /><br /> **False** : Données de texte dans le fichier plat ne sont pas qualifiées.|  
|**Nom**|Précisez un nom de colonne. La valeur par défaut est une liste numérotée de colonnes. Vous pouvez toutefois indiquer un nom descriptif unique de votre choix.|  
|**DataScale**|Spécifiez l'échelle des données numériques. L'échelle est le nombre de décimales. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Sélectionnez un délimiteur de colonnes dans la liste des séparateurs de colonnes disponibles. Veillez à choisir un caractère de séparation qu'il est peu probable de rencontrer dans le texte. Cette valeur est ignorée dans le cas des colonnes à largeur fixe.<br /><br /> **{CR}{LF}**  : les colonnes sont délimitées par une combinaison retour chariot/saut de ligne<br /><br /> **{CR}**  : les colonnes sont séparées par un retour chariot<br /><br /> **{LF}**  : les colonnes sont séparées par un saut de ligne<br /><br /> **Point-virgule {;}**  : les colonnes sont délimitées par un point-virgule<br /><br /> **Deux-points {:}**  : les colonnes sont délimitées par un deux-points<br /><br /> **Virgule {,}**  : les colonnes sont délimitées par une virgule<br /><br /> **Tabulation {t}**  : les colonnes sont délimitées par une tabulation<br /><br /> **Barre verticale {&#124;}**  : les colonnes sont délimitées par une barre verticale|  
|**DataPrecision**|Spécifiez la précision des données numériques. La précision indique le nombre total de chiffres. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).|  
|**InputColumnWidth**|Indiquez une valeur spécifiant la largeur de colonne en nombre d'octets. Pour les fichiers Unicode, cette valeur est exprimée en nombre de caractères. Cette valeur est ignorée dans le cas des colonnes délimitées.<br /><br /> **Remarque** : Dans le modèle objet, le nom de cette propriété est ColumnWidth.|  
  
 **Nouveau**  
 Ajoutez une nouvelle colonne en cliquant sur **Nouveau**. Par défaut, ce **nouveau** bouton ajoute une nouvelle colonne à la fin de la liste. Il comporte également une liste déroulante avec les options disponibles suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**Ajouter une colonne**|Ajoute une colonne à la fin de la liste.|  
|**Insérer avant**|Insère une nouvelle colonne avant la colonne sélectionnée.|  
|**Insérer après**|Insère une nouvelle colonne après la colonne sélectionnée.|  
  
 **Supprimer**  
 Sélectionnez une colonne, puis supprimez-la en cliquant sur **Supprimer**.  
  
 **Suggérer les types**  
 Utilisez la boîte de dialogue **Suggérer les types de colonnes** pour évaluer un échantillon de données provenant du premier fichier sélectionné et pour obtenir des suggestions concernant le type de données et la longueur de chaque colonne. Pour plus d’informations, consultez [Référence de l’interface utilisateur de la boîte de dialogue Suggérer les types de colonnes](connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Colonnes&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats multiples &#40;page Aperçu&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)  
  
  
