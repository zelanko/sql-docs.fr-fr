---
title: SQLGetStmtAttr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cfd74525cda5946fb7c86f21638437ee91c3ac7f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211190"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client étend le SQLGetStmtAttr pour exposer les attributs d’instruction spécifiques au pilote.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) répertorie les attributs d’instruction qui sont toutes deux lire et écrire. Cette rubrique dresse la liste des attributs d'instruction accessibles en lecture seule.  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 L'attribut SQL_SOPT_SS_CURRENT_COMMAND expose la commande active d'un lot de commandes. La valeur retournée est un entier qui spécifie l'emplacement de la commande dans le lot. La valeur de *ValuePtr* est de type SQLLEN.  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 L’attribut SQL_SOPT_SS_NOCOUNT_STATUS indique le paramètre actuel de la NOCOUNT option, si les contrôles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signale le nombre de lignes affectées par une instruction lorsque [SQLRowCount](sqlrowcount.md) est appelée. La valeur de *ValuePtr* est de type SQLLEN.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT a la valeur OFF. SQLRowCount retourne le nombre de lignes affectées.|  
|SQL_NC_ON|NOCOUNT a la valeur ON. Le nombre de lignes affectées n’est pas retourné par SQLRowCount et la valeur retournée est 0.|  
  
 Si SQLRowCount retourne 0, l’application doit tester SQL_SOPT_SS_NOCOUNT_STATUS. Si SQL_NC_ON est retourné, la valeur 0 de SQLRowCount indique uniquement que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas retourné un nombre de lignes. Si SQL_NC_OFF est retourné, cela signifie que NOCOUNT est désactivée et la valeur 0 de SQLRowCount indique que l’instruction n’a affecté aucune ligne.  
  
 Les applications ne doivent pas afficher la valeur de SQLRowCount quand SQL_SOPT_SS_NOCOUNT_STATUS a la valeur SQL_NC_OFF. Les lots ou procédures stockées de grande taille peuvent contenir plusieurs instructions SET NOCOUNT. Il n'est donc pas possible de supposer que SQL_SOPT_SS_NOCOUNT_STATUS reste constant. Cette option doit être testée chaque fois que SQLRowCount retourne 0.  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 L'attribut SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT retourne le texte du message pour la demande de notification de requête.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr et paramètres table  
 SQLGetStmtAttr peut être appelé pour obtenir la valeur de SQL_SOPT_SS_PARAM_FOCUS dans le descripteur de paramètre d’application (APD) lorsque vous travaillez avec des paramètres table. Pour plus d’informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSetStmtAttr, fonction](http://go.microsoft.com/fwlink/?LinkId=59370)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
