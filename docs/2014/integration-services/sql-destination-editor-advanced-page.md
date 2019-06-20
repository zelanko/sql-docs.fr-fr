---
title: Éditeur de Destination SQL (Page avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 087f32510b65d7ea505bc4bf816a5ca9edcfe82d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66055462"
---
# <a name="sql-destination-editor-advanced-page"></a>Éditeur de destination SQL (page Avancé)
  Utilisez la page **Avancé** de la boîte de dialogue **Éditeur de destination SQL** pour spécifier les options avancées pour l’insertion en bloc.  
  
 Pour en savoir plus sur la destination pour SQL Server, consultez [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Options  
 **Conserver l'identité**  
 Spécifie si la tâche doit insérer des valeurs dans les colonnes d'identité. La valeur par défaut de cette propriété est `False`.  
  
 **Conserver les valeurs NULL**  
 Spécifie si la tâche doit conserver les valeurs NULL. La valeur par défaut de cette propriété est `False`.  
  
 **Verrou de table**  
 Spécifie si la table est verrouillée lors du chargement des données. La valeur par défaut de cette propriété est `True`.  
  
 **Contraintes de validation**  
 Spécifie si la tâche doit vérifier les contraintes. La valeur par défaut de cette propriété est `True`.  
  
 **Exécuter les déclencheurs**  
 Spécifie si l'insertion en bloc doit exécuter les déclencheurs sur les tables. La valeur par défaut de cette propriété est `False`.  
  
 **Première ligne**  
 Spécifie la première ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés** , **l’Éditeur avancé**et le modèle objet.  
  
 **Dernière ligne**  
 Spécifie la dernière ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés** , **l’Éditeur avancé**et le modèle objet.  
  
 **Nombre maximum d'erreurs**  
 Spécifie le nombre d'erreurs au-delà duquel l'insertion en bloc s'arrête. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur ne lui a été assignée.  
  
> [!NOTE]  
>  Effacez la zone de texte dans **l’Éditeur de destination SQL** pour indiquer que vous ne voulez pas assigner de valeur à cette propriété. Utilisez -1 dans la fenêtre **Propriétés** , **l’Éditeur avancé**et le modèle objet.  
  
 **Délai d'expiration**  
 Spécifie le nombre de secondes pouvant s'écouler avant l'expiration de l'insertion en bloc.  
  
 **Ordre des colonnes**  
 Tapez le nom des colonnes de tri. Chaque colonne peut être triée par ordre croissant ou décroissant. Si vous utilisez plusieurs colonnes de tri, délimitez la liste par des virgules.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination SQL &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md)   
 [Éditeur de destination SQL &#40;page Mappages&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Charger des données en masse à l’aide de la destination SQL Server](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
