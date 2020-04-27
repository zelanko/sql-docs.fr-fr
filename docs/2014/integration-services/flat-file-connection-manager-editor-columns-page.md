---
title: Éditeur du gestionnaire de connexions de fichiers plats (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columns.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 40ce7537-abd0-4973-97fd-6ccb90fddfa0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6dad0ca9855cfad8811b1598356ab624ea3fc5ca
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058726"
---
# <a name="flat-file-connection-manager-editor-columns-page"></a>Éditeur du gestionnaire de connexions de fichiers plats (page Colonnes)
  La page **Colonnes** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** vous permet de spécifier les informations de ligne et de colonne, ainsi que d'afficher un aperçu du fichier.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers plats, consultez [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="static-options"></a>Options statiques  
 **Nom du gestionnaire de connexions**  
 Fournit un nom unique pour la connexion de fichiers plats du flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Description**  
 Décrit la connexion. Il est recommandé d'indiquer ici l'usage auquel la connexion est destinée, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
## <a name="flat-file-format-dynamic-options"></a>Options dynamiques de format de fichier plat  
  
### <a name="format--delimited"></a>Format = Délimité  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**CR**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Point{,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Délimiteur de colonne**  
 Effectuez une sélection dans la liste des séparateurs de colonnes disponibles ou entrez le texte du séparateur.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les colonnes sont délimitées par une combinaison retour chariot-saut de ligne.|  
|**CR**|Les colonnes sont séparées par un retour chariot.|  
|**{LF}**|Les colonnes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les colonnes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les colonnes sont séparées par un deux-points.|  
|**Point{,}**|Les colonnes sont séparées par une virgule.|  
|**Tabulation {t}**|Les colonnes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les colonnes sont séparées par une barre verticale.|  
  
 **Actualisation**  
 Affichez les résultats des modifications des séparateurs en cliquant sur **Actualiser**. Il ne devient visible qu'après avoir changé d'autres options de connexion.  
  
 **Aperçu des lignes**  
 Affichez les données d'exemple dans le fichier plat, divisées en colonnes et en lignes à l'aide des options sélectionnées.  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### <a name="format--fixed-width"></a>Format = Largeur fixe  
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne rouge vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Largeur de ligne**  
 Spécifiez la largeur de la ligne avant d'ajouter des séparateurs pour des colonnes distinctes. Vous pouvez également faire glisser la ligne rouge verticale dans la fenêtre d'aperçu pour marquer la fin de la ligne. La valeur de la largeur de ligne est automatiquement mise à jour.  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
### <a name="format--ragged-right"></a>Format = En drapeau à droite  
  
> [!NOTE]  
>  Les fichiers en drapeau à droite sont des fichiers dans lesquels chaque colonne a une largeur fixe, à l'exception de la dernière colonne. Un séparateur de lignes s'applique.  
  
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne rouge vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**CR**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Point{,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Réinitialiser les colonnes**  
 Cliquez sur **Réinitialiser les colonnes**pour supprimer toutes les colonnes à l’exception de celles d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
