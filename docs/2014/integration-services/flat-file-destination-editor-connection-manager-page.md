---
title: Éditeur de destination de fichier plat (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledestadapter.connection.f1
helpviewer_keywords:
- Flat File Destination Editor
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 429ba1f8a12a4bd574a8304d18311a6e6e4efc79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058695"
---
# <a name="flat-file-destination-editor-connection-manager-page"></a>Éditeur de destination de fichier plat (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination de fichier plat** pour sélectionner la connexion de fichier plat de la destination et spécifier si elle doit remplacer le fichier de destination existant ou lui être ajoutée. La destination de fichier plat écrit ses données dans un fichier texte. Ce fichier texte peut être d'un format délimité, à largeur fixe avec séparateur de lignes, ou en drapeau à droite.  
  
 Pour en savoir plus sur la destination de fichier plat, consultez [Flat File Destination](data-flow/flat-file-destination.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions de fichiers plats**  
 Sélectionnez un gestionnaire de connexions existant dans la zone de liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez une connexion à l’aide des boîtes de dialogue **Format de fichier plat** et **Éditeur du gestionnaire de connexions de fichiers plats** .  
  
 En plus des formats de fichier plat standard (délimité, largeur fixe et en drapeau à droite), la boîte de dialogue **Format de fichier plat** contient une quatrième option : **Largeur fixe avec séparateurs de lignes**. Cette option représente un cas particulier du format en drapeau à droite dans lequel [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ajoute une colonne factice comme dernière colonne de données. Cette colonne factice garantit que la dernière colonne a une largeur fixe.  
  
 L'option **Largeur fixe avec séparateurs de lignes** n'est pas disponible dans l' **éditeur du gestionnaire de connexions de fichiers plats**. Le cas échéant, vous pouvez émuler cette option dans l'éditeur. Pour émuler cette option, dans la page **Général** de l' **éditeur du gestionnaire de connexions de fichiers plats**, pour **Format**, sélectionnez **En drapeau à droite**. Puis, dans la page **Avancé** de l'éditeur, ajoutez une colonne factice comme dernière colonne de données.  
  
 **Remplacer les données du fichier**  
 Précisez si le fichier existant doit être remplacé ou si les données doivent lui être ajoutées.  
  
 **Titre**  
 Tapez un bloc de texte à insérer dans le fichier avant l'écriture des données. Utilisez cette option pour inclure des informations supplémentaires, telles que des titres de colonne.  
  
 **Préversion**  
 Affichez un aperçu des résultats à partir de la boîte de dialogue **Vue de données** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination de fichier plat &#40;page Mappages&#41;](../../2014/integration-services/flat-file-destination-editor-mappings-page.md)  
  
  
