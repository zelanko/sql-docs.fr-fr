---
title: Éditeur de transformation de la table des caractères | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 76f2c5e517ca81ae667df3efa6ccd2f49384f090
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060981"
---
# <a name="character-map-transformation-editor"></a>Éditeur de transformation de la table des caractères
  Utilisez la boîte de dialogue **Éditeur de transformation de la table des caractères** pour sélectionner les fonctions de chaîne à appliquer aux données de colonne, et indiquer si le mappage est une modification sur place ou s’il est ajouté sous la forme d’une nouvelle colonne.  
  
 Pour en savoir plus sur la transformation de la table des caractères, consultez [Character Map Transformation](data-flow/transformations/character-map-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d’entrée disponibles**  
 Activez les cases à cocher pour sélectionner les colonnes à transformer en utilisant des fonctions de chaîne. Vos sélections figurent dans le tableau ci-dessous.  
  
 **Colonne d'entrée**  
 Affiche les colonnes d'entrée sélectionnées dans le tableau ci-dessus. Vous pouvez également changer ou supprimer une sélection en utilisant la liste des colonnes d'entrée disponibles.  
  
 **Destination**  
 Indiquez si vous voulez enregistrer le résultat des opérations de chaîne sur place en utilisant la colonne existante, ou enregistrer les données modifiées sous la forme d'une nouvelle colonne.  
  
|Value|Description|  
|-----------|-----------------|  
|Nouvelle colonne|Enregistre les données dans une nouvelle colonne. Définissez le nom de la colonne sous **Alias de sortie**.|  
|Modification sur place|Enregistre les données modifiées dans la colonne existante.|  
  
 **opération**  
 Dans la liste, sélectionnez les fonctions de chaîne à appliquer aux données de la colonne.  
  
|Value|Description|  
|-----------|-----------------|  
|Minuscules|Convertit les caractères en minuscules.|  
|Majuscules|Convertit les caractères en majuscules|  
|Inversion d'octet|Convertit en inversant l'ordre d'octet.|  
|Hiragana|Convertit les caractères japonais katakana en caractères hiragana.|  
|Katakana|Convertit les caractères japonais hiragana en caractères katakana.|  
|Demi-chasse|Convertit les caractères pleine chasse en caractères demi-chasse.|  
|Pleine chasse|Convertit les caractères demi-chasse en caractères pleine chasse.|  
|Casse linguistique|Applique des règles de casse linguistique (mappage de casse simple Unicode pour le turc et d'autres paramètres locaux) à la place des règles système.|  
|Chinois simplifié|Convertit les caractères chinois traditionnels en caractères chinois simplifié.|  
|Chinois traditionnel|Convertit les caractères chinois simplifié en caractères chinois traditionnel.|  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. La valeur par défaut est **Copie de** suivi du nom de la colonne d'entrée. Toutefois, vous pouvez choisir n'importe quel nom descriptif unique.  
  
 **Configurer la sortie d’erreur**  
 Utilisez la boîte de dialogue [Configurer la sortie d’erreur](../../2014/integration-services/configure-error-output.md) pour définir les options de gestion des erreurs de cette transformation.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
