---
title: Fonction SQLRateConnection (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d29033460a7f89fc4a8b1c371a4d32bdf94a2a05
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288879"
---
# <a name="sqlrateconnection-function"></a>SQLRateConnection, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLRateConnection** détermine si un conducteur peut réutiliser une connexion existante dans le pool de connexion.  
  
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
 [Entrée] Une poignée de jet représentant la nouvelle demande de connexion d’application.  
  
 *hCandidateConnection*  
 [Entrée] La connexion existante dans le pool de connexion. La connexion doit être dans un état ouvert.  
  
 *fRequiredTransactionEnlistment*  
 [Entrée] Si VRAI, la réutiliser *hCandidateConnection* de la connexion existante pour la nouvelle demande de connexion (*hRequest*) nécessite un enrôlement supplémentaire.  
  
 *transId transId*  
 [Entrée] Si *fRequiredTransactionEn l’inscription* est VRAI, *transId* représente la transaction DTC que la demande enrôlera. Si *fRequiredTransactionEnlistment* est FALSE, *transId* sera ignoré.  
  
 *pRating*  
 [Sortie] *hCandidateConnection*'s reuse rating for the *hRequest*. Cette note se situera entre 0 et 100 (inclusive).  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_ERROR, ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Le gestionnaire de conducteur ne traitera pas les informations diagnostiques retournées de cette fonction.  
  
## <a name="remarks"></a>Notes  
 **SQLRateConnection** produit un score compris entre 0 et 100 (inclus) indiquant dans quelle mesure une connexion existante correspond à la demande.  
  
|Score|Signification (lorsque SQL_SUCCESS est retournée)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* ne doit pas être réutilisé pour le *hRequest*.|  
|Toutes les valeurs entre 1 et 98 (inclusivement)|Plus le score est élevé, plus le match *hCandidateConnection* avec *hRequest*est proche.|  
|99|Il n’y a que des décalages dans les attributs insignifiants.  Le gestionnaire de pilote doit arrêter la boucle de notation.|  
|100|Match parfait.  Le gestionnaire de pilote doit arrêter la boucle de notation.|  
|Toute autre valeur supérieure à 100|*hCandidateConnection* est marqué comme mort et il ne sera pas réutilisé, même dans une demande de connexion future.|  
  
 Le gestionnaire de conducteur marquera une connexion comme morte si le code de retour est autre chose que SQL_SUCCESS (y compris SQL_SUCCESS_WITH_INFO) ou si la cote est supérieure à 100. Cette connexion morte ne sera pas réutilisée (même dans les futures demandes de connexion) et sera éventuellement chronométrée après le passage de CPTimeout. Le gestionnaire de conducteur continuera de trouver une autre connexion de la piscine au tarif.  
  
 Si le gestionnaire de chauffeur a réutilisé une connexion dont le score est strictement inférieur à 100 (dont 99), le gestionnaire de pilote appellera SQLSetConnectAttr (SQL_ATTR_DBC_INFO_TOKEN) pour réinitialiser la connexion dans l’État demandé par la demande. Le conducteur ne doit pas réinitialiser la connexion dans cet appel de fonction.  
  
 Si *fRequiredTransactionEnlistment* est VRAI, la réutilation *hCandidateConnection* nécessite un enrôlement supplémentaire *(transId* ! ' NULL) ou unnlistment *(transId* 'NULL). Cela indique le coût de réutilisation d’une connexion et si le conducteur doit enrôler / non-liste de la connexion si elle va réutiliser la connexion. Si *fRequireTransactionEnlistment* est FALSE, le conducteur doit ignorer la valeur de *transId*.  
  
 Le Driver Manager garantit que la poignée mère HENV de *hRequest* et *hCandidateConnection* sont les mêmes. Le Driver Manager garantit que l’ID de piscine associé à *hRequest* et *hCandidateConnection* sont les mêmes.  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
