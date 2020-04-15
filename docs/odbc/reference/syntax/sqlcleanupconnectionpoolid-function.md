---
title: Fonction SQLCleanupConnectionPoolID (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a74a92cc05ecd41e99ff87642c7fe3ee527e0c98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301319"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLCleanupConnectionPoolID** informe un conducteur qu’une pièce d’identité de piscine a été chronométrée. Une pièce d’identité de piscine peut chronométrer chaque fois que toutes les connexions dans une piscine associée à cette pièce d’identité de piscine ont été chronométrées. Voir [Pooling dans les composants Microsoft Data Access](https://msdn.microsoft.com/library/ms810829.aspx) pour plus d’informations sur le délai d’attente de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironnementHandle*  
 [Entrée] La poignée de l’environnement de la piscine.  
  
 *PoolID (PoolID)*  
 [Entrée] La piscine associée à la carte d’identité de la piscine qui a été chronométré.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Le gestionnaire de chauffeur ne traitera pas les informations diagnostiques retournées de **SQLCleanupConnectionPoolID**.  
  
 Une application ne peut pas recevoir le message d’erreur retourné par le conducteur.  
  
## <a name="remarks"></a>Notes  
 **SQLCleanupConnectionPoolID** peut être appelé à tout moment, mais le gestionnaire de conducteur garantit qu’aucun autre thread n’appelle simultanément **SQLGetPoolID** et aucun autre thread n’appelle simultanément **SQLRateConnection** et **SQLPoolConnect** avec un jeton d’information de connexion attribué avec ce id de piscine. Par conséquent, le conducteur doit s’assurer que cette fonction est sans danger de thread.  
  
 Un conducteur peut nettoyer les ressources associées à l’id de la piscine.  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
