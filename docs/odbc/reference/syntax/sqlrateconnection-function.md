---
title: Sqlrateconnection, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74d7e2c52167682f0993006db3a1125ca741cf35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053641"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3,81 ODBC : ODBC  
  
 **Résumé**  
 **SQLRateConnection** détermine si un pilote peut réutiliser une connexion existante dans le pool de connexions.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Arguments  
 *hRequest*  
 [Entrée] Un handle de jeton qui représente la nouvelle demande de connexion d’application.  
  
 *hCandidateConnection*  
 [Entrée] La connexion existante dans le pool de connexions. La connexion doit être dans un état ouvert.  
  
 *fRequiredTransactionEnlistment*  
 [Entrée] Si la valeur est TRUE, réutilisation de la connexion existante *hCandidateConnection* pour la nouvelle demande de connexion (*hRequest*) nécessite une inscription supplémentaire.  
  
 *transId*  
 [Entrée] Si *fRequiredTransactionEnlistment* a la valeur TRUE, *ID transaction* représente la transaction DTC figurant à la demande. Si *fRequiredTransactionEnlistment* est FALSE, *ID transaction* sera ignoré.  
  
 *pRating*  
 [Sortie] *hCandidateConnection*réutilisation note de pour le *hRequest*. Cette évaluation sera comprise entre 0 et 100 (inclus).  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Le Gestionnaire de pilotes ne traitera pas les informations de diagnostic retournées par cette fonction.  
  
## <a name="remarks"></a>Notes  
 **SQLRateConnection** génère un score compris entre 0 et 100 (inclus), indiquant la manière dont une connexion existante correspond à la demande.  
  
|Score|Signification (lorsque la valeur SQL_SUCCESS est retournée)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* ne doivent pas être réutilisés pour le *hRequest*.|  
|Toute valeur comprise entre 1 et 98 (inclus)|Plus le score est élevé, plus que *hCandidateConnection* correspond à la *hRequest*.|  
|99|Il y a des incompatibilités d’uniquement dans les attributs non significatifs.  Le Gestionnaire de pilotes doit s’arrêter la boucle de contrôle d’accès.|  
|100|Correspondance parfaite.  Le Gestionnaire de pilotes doit s’arrêter la boucle de contrôle d’accès.|  
|Toute autre valeur supérieure à 100|*hCandidateConnection* est marqué comme inactif et il ne seront pas réutilisées même dans une demande de connexion ultérieures.|  
  
 Le Gestionnaire de pilotes marque une connexion comme étant inactif si le code de retour est autre que SQL_SUCCESS (y compris SQL_SUCCESS_WITH_INFO) ou l’évaluation est supérieure à 100. Cette connexion ne sera pas réutilisée (même dans les demandes de connexion ultérieures) et finalement expire après que CPTimeout transmet. Le Gestionnaire de pilotes continueront à trouver une autre connexion à partir du pool au taux.  
  
 Si le Gestionnaire de pilotes réutiliser une connexion dont le score est strictement inférieur à 100 (y compris les 99), le Gestionnaire de pilotes appelle SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) pour réinitialiser la connexion dans l’état demandé par l’application. Le pilote ne doit pas réinitialiser la connexion dans cet appel de fonction.  
  
 Si *fRequiredTransactionEnlistment* est TRUE, la réutilisation *hCandidateConnection* a besoin d’une inscription supplémentaire (*ID transaction* ! = NULL) ou unenlistment ( *ID transaction* == NULL). Cela indique le coût de réutiliser une connexion et si le pilote doit inscrire / désinscrire la connexion si elle va réutiliser la connexion. Si *fRequireTransactionEnlistment* est FALSE, pilote doit ignorer la valeur de *ID transaction*.  
  
 Le Gestionnaire de pilotes garantit que le parent HENV gérer de *hRequest* et *hCandidateConnection* sont les mêmes. Le Gestionnaire de pilotes garantit que l’ID du pool associé à *hRequest* et *hCandidateConnection* sont les mêmes.  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
