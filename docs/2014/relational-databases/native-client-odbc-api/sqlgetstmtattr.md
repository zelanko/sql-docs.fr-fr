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
author: rothja
ms.author: jroth
ms.openlocfilehash: b7bd7f5e1e04254a5fb6f2a228191b3ff7845af4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022059"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client étend SQLGetStmtAttr pour exposer des attributs d’instruction spécifiques au pilote.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) répertorie les attributs d'instruction qui sont à la fois accessibles en lecture et en écriture. Cette rubrique dresse la liste des attributs d'instruction accessibles en lecture seule.  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 L'attribut SQL_SOPT_SS_CURRENT_COMMAND expose la commande active d'un lot de commandes. La valeur retournée est un entier qui spécifie l'emplacement de la commande dans le lot. La valeur de *ValuePtr* est de type SQLLEN.  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 L'attribut SQL_SOPT_SS_NOCOUNT_STATUS indique le paramètre actif de l'option NOCOUNT, qui contrôle si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signale le nombre de lignes affectées par une instruction lorsque [SQLRowCount](sqlrowcount.md) est appelé. La valeur de *ValuePtr* est de type SQLLEN.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT a la valeur OFF. SQLRowCount retourne le nombre de lignes affectées.|  
|SQL_NC_ON|NOCOUNT a la valeur ON. Le nombre de lignes affectées n’est pas retourné par SQLRowCount et la valeur retournée est 0.|  
  
 Si SQLRowCount retourne 0, l’application doit tester SQL_SOPT_SS_NOCOUNT_STATUS. Si SQL_NC_ON est retourné, la valeur 0 de SQLRowCount indique uniquement que n' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a pas retourné de nombre de lignes. Si SQL_NC_OFF est retourné, cela signifie que l'option NOCOUNT est désactivée et la valeur 0 de SQLRowCount indique que l'instruction n'a affecté aucune ligne.  
  
 Les applications ne doivent pas afficher la valeur de SQLRowCount quand SQL_SOPT_SS_NOCOUNT_STATUS a la valeur SQL_NC_OFF. Les lots ou procédures stockées de grande taille peuvent contenir plusieurs instructions SET NOCOUNT. Il n'est donc pas possible de supposer que SQL_SOPT_SS_NOCOUNT_STATUS reste constant. Cette option doit être testée à chaque fois que SQLRowCount retourne 0.  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 L'attribut SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT retourne le texte du message pour la demande de notification de requête.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr et paramètres table  
 SQLGetStmtAttr peut être appelé pour extraire la valeur de SQL_SOPT_SS_PARAM_FOCUS dans le descripteur de paramètre d’application (APD) lors de l’utilisation de paramètres table. Pour plus d'informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLSetStmtAttr, fonction](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
