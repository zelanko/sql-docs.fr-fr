---
title: Éditeur de source de fichier plat (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: cef1d05182edd02c9b0cdb0e6237c09473041dde
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966426"
---
# <a name="flat-file-source-editor-connection-manager-page"></a>Éditeur de source de fichier plat (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source de fichier plat** pour sélectionner le gestionnaire de connexions de fichiers plats qui sera utilisé par la source de fichier plat. La source de fichier plat lit les données d'un fichier texte qui peut être au format délimité, à largeur fixe ou mixte.  
  
 Une source de fichier plat peut utiliser l'un des types de gestionnaires de connexions suivants :  
  
-   Un gestionnaire de connexions de fichiers plats si la source est un fichier plat unique. Pour plus d'informations, consultez [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
-   Un gestionnaire de connexions de fichiers plats multiples si la source se compose de fichiers plats multiples et si la tâche de flux de données se trouve dans un conteneur de boucles (conteneur de boucles For, par exemple). Dans chaque boucle du conteneur, la source de fichier plat charge les données à partir du nom de fichier suivant fourni par le gestionnaire de connexions de fichiers plats multiples. Pour plus d’informations, consultez [Gestionnaire de connexion de fichiers plats multiples](connection-manager/multiple-flat-files-connection-manager.md).  
  
 Pour en savoir plus sur la source de fichier plat, consultez [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions de fichiers plats**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez un gestionnaire de connexions en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** .  
  
 **Conserver les valeurs NULL de la source comme valeurs NULL dans le flux de données**  
 Indique s'il faut conserver les valeurs NULL lorsque les données sont extraites. La valeur par défaut de cette propriété est **false**. Lorsque cette propriété a la valeur `alse`, la source de fichier plat remplace les valeurs NULL des données sources par les valeurs par défaut appropriées pour chaque colonne, par exemple des chaînes vides pour les colonnes de chaînes et zéro pour les colonnes numériques.  
  
 **Préversion**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Vue de données** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source de fichier plat &#40;page colonnes&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md)   
 [Éditeur de source de fichier plat &#40;page sortie d’erreur&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Gestionnaire de connexions de fichiers plats](connection-manager/file-connection-manager.md)  
  
  
