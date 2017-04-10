---
title: "&#201;diteur de destination SQL (page Avanc&#233;) | Microsoft Docs"
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
  - "sql13.dts.designer.sqlserverdestadapter.advanced.f1"
helpviewer_keywords: 
  - "Éditeur de destination SQL Server"
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# &#201;diteur de destination SQL (page Avanc&#233;)
  Utilisez la page **Avancé** de la boîte de dialogue **Éditeur de destination SQL** pour spécifier les options avancées pour l’insertion en bloc.  
  
 Pour en savoir plus sur la destination pour SQL Server, consultez [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## Options  
 **Conserver l'identité**  
 Spécifie si la tâche doit insérer des valeurs dans les colonnes d'identité. La valeur par défaut de cette propriété est **False**.  
  
 **Conserver les valeurs NULL**  
 Spécifie si la tâche doit conserver les valeurs NULL. La valeur par défaut de cette propriété est **False**.  
  
 **Verrou de table**  
 Spécifie si la table est verrouillée lors du chargement des données. La valeur par défaut de cette propriété est **True**.  
  
 **Contraintes de validation**  
 Spécifie si la tâche doit vérifier les contraintes. La valeur par défaut de cette propriété est **True**.  
  
 **Exécuter les déclencheurs**  
 Spécifie si l'insertion en bloc doit exécuter les déclencheurs sur les tables. La valeur par défaut de cette propriété est **False**.  
  
 **Première ligne**  
 Spécifie la première ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés**, **l’Éditeur avancé** et le modèle objet.  
  
 **Dernière ligne**  
 Spécifie la dernière ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés**, **l’Éditeur avancé** et le modèle objet.  
  
 **Nombre maximum d'erreurs**  
 Spécifie le nombre d'erreurs au-delà duquel l'insertion en bloc s'arrête. La valeur par défaut de cette propriété est **–1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés**, **l’Éditeur avancé** et le modèle objet.  
  
 **Délai d'expiration**  
 Spécifie le nombre de secondes pouvant s'écouler avant l'expiration de l'insertion en bloc.  
  
 **Ordre des colonnes**  
 Tapez le nom des colonnes de tri. Chaque colonne peut être triée par ordre croissant ou décroissant. Si vous utilisez plusieurs colonnes de tri, délimitez la liste par des virgules.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination SQL &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/sql-destination-editor-connection-manager-page.md)   
 [Éditeur de destination SQL &#40;page Mappages&#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)   
 [Charger des données en masse à l'aide de la destination SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  