---
title: "&#201;diteur de source de fichier plat (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.flatfilesourceadapter.connection.f1"
helpviewer_keywords: 
  - "Éditeur de source de fichier plat"
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# &#201;diteur de source de fichier plat (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source de fichier plat** pour sélectionner le gestionnaire de connexions de fichiers plats qui sera utilisé par la source de fichier plat. La source de fichier plat lit les données d'un fichier texte qui peut être au format délimité, à largeur fixe ou mixte.  
  
 Une source de fichier plat peut utiliser l'un des types de gestionnaires de connexions suivants :  
  
-   Un gestionnaire de connexions de fichiers plats si la source est un fichier plat unique. Pour plus d'informations, consultez [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
-   Un gestionnaire de connexions de fichiers plats multiples si la source se compose de fichiers plats multiples et si la tâche de flux de données se trouve dans un conteneur de boucles (conteneur de boucles For, par exemple). Dans chaque boucle du conteneur, la source de fichier plat charge les données à partir du nom de fichier suivant fourni par le gestionnaire de connexions de fichiers plats multiples. Pour plus d’informations, consultez [Gestionnaire de connexion de fichiers plats multiples](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md).  
  
 Pour en savoir plus sur la source de fichier plat, consultez [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
## Options  
 **Gestionnaire de connexions de fichiers plats**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez un gestionnaire de connexions en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats**.  
  
 **Conserver les valeurs NULL de la source comme valeurs NULL dans le flux de données**  
 Indique s'il faut conserver les valeurs NULL lorsque les données sont extraites. La valeur par défaut de cette propriété est **False**. Quand cette propriété a la valeur **false**, la source de fichier plat remplace les valeurs NULL des données sources par les valeurs par défaut appropriées pour chaque colonne, par exemple des chaînes vides pour les colonnes de chaînes et zéro pour les colonnes numériques.  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Vue de données**. L'aperçu peut afficher jusqu'à 200 lignes.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source de fichier plat &#40;page Colonnes&#41;](../../integration-services/data-flow/flat-file-source-editor-columns-page.md)   
 [Éditeur de source de fichier plat &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)   
 [Gestionnaire de connexions de fichiers plats](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  