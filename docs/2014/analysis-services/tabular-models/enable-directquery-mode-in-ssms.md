---
title: Configurer l’accès de DirectQuery pour une base de données de modèle tabulaire ou de mémoire | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c91dd8529fa6ddfb111ebb87cb84d87a55d3a709
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152207"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Configurer l'accès In-Memory ou DirectQuery pour une base de données model tabulaire
  Cette rubrique explique comment modifier les propriétés de connexion d'un modèle tabulaire qui a déjà été déployé afin d'activer l'utilisation du modèle en mode de requête directe.  
  
 Pour plus d’informations sur ces propriétés et la configuration pour les scénarios les plus courants, consultez [les scénarios de déploiement DirectQuery &#40;tabulaire SSAS&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Spécifications  
 L'activation de l'utilisation du mode de requête directe sur un modèle tabulaire est un processus qui implique plusieurs étapes. Il le faut :  
  
1.  Vérifiez que le modèle n'a pas de fonctionnalités susceptibles de provoquer des erreurs de validation en mode de requête directe.  
  
2.  Modifiez le mode de stockage sur le modèle pour prendre en charge la requête directe.  
  
3.  Déployez le modèle dans un mode qui prend en charge les requêtes en mode hybride ou en mode de requête directe pur.  
  
4.  Modifiez la chaîne de connexion dans la base de données déployée pour prendre en charge le mode de requête directe.  
  
 Cette rubrique suppose que vous avez créé et validé votre modèle, et que vous devez uniquement activer l'accès aux requêtes directes à partir d'un client tel que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Modifier les propriétés de chaîne de connexion du modèle  
  
1.  Dans SQL Server Management Studio, ouvrez l'instance sur laquelle vous avez déployé le modèle.  
  
2.  Dans l’Explorateur d’objets, cliquez sur le nom de la base de données model, puis sélectionnez **propriétés**.  
  
3.  Recherchez la propriété **DirectQueryMode**. Pour activer l'utilisation de la source de données relationnelles, cette propriété doit être définie avec l'une des valeurs suivantes :  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  