---
description: Générer des tables miroir et des instances de capture de données modifiées
title: Générer des tables miroir et des instances de capture CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8340ef153f815d3073edaf4f9a13e99e1e9f67
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88394805"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>Générer des tables miroir et des instances de capture de données modifiées

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Utiliser la page Générer des tables miroir pour générer les tables miroir des tables incluses dans l'instance de capture de données modifiées  
  
 Cliquez sur **Exécuter** pour créer les tables miroir. La progression de la création de chaque table s'affiche, ainsi qu'un message pour vous indiquer si chaque table miroir s'est terminée correctement ou avec des erreurs. Si des erreurs se produisent, cliquez sur **Détails** pour afficher la boîte de dialogue contenant une explication de l'erreur.  
  
 En cas d'échec de la création de l'une des tables, vous pouvez choisir de continuer ou de supprimer toutes les tables ayant échoué avant de continuer. Une fois l'exécution de l'Assistant terminée, vous pouvez décider de corriger la table dans la base de données source Oracle ou de ne pas l'utiliser dans l'instance de capture de données modifiées. Si vous corrigez la table, vous pouvez l'ajouter lorsque vous [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
 Cliquez sur **Suivant** pour ouvrir la page [Finish](../../integration-services/change-data-capture/finish.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
