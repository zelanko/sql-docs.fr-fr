---
title: "&#201;diteur de transformation de la table des caract&#232;res | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.charactermaptransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de la table des caractères"
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;diteur de transformation de la table des caract&#232;res
  Utilisez la boîte de dialogue **Éditeur de transformation de la table des caractères** pour sélectionner les fonctions de chaîne à appliquer aux données de colonne, et indiquer si le mappage est une modification sur place ou s’il est ajouté sous la forme d’une nouvelle colonne.  
  
 Pour en savoir plus sur la transformation de la table des caractères, consultez [Character Map Transformation](../../../integration-services/data-flow/transformations/character-map-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 Activez les cases à cocher pour sélectionner les colonnes à transformer en utilisant des fonctions de chaîne. Vos sélections figurent dans le tableau ci-dessous.  
  
 **Colonne d'entrée**  
 Affiche les colonnes d'entrée sélectionnées dans le tableau ci-dessus. Vous pouvez également changer ou supprimer une sélection en utilisant la liste des colonnes d'entrée disponibles.  
  
 **Destination**  
 Indiquez si vous voulez enregistrer le résultat des opérations de chaîne sur place en utilisant la colonne existante, ou enregistrer les données modifiées sous la forme d'une nouvelle colonne.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Nouvelle colonne|Enregistre les données dans une nouvelle colonne. Définissez le nom de la colonne sous **Alias de sortie**.|  
|Modification sur place|Enregistre les données modifiées dans la colonne existante.|  
  
 **Opération**  
 Dans la liste, sélectionnez les fonctions de chaîne à appliquer aux données de la colonne.  
  
|Valeur|Description|  
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
  
 **Configurer la sortie d'erreur**  
 Utilisez la boîte de dialogue [Configurer la sortie d’erreur](../Topic/Configure%20Error%20Output.md) pour définir les options de gestion des erreurs de cette transformation.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  