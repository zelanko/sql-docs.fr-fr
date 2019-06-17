---
title: Appeler des procédures stockées (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58e5160065847d5729548702b5f1d65eb31bf694
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200266"
---
# <a name="call-stored-procedures-odbc"></a>Appeler des procédures stockées (ODBC)
  Lorsqu’une instruction SQL appelle une procédure stockée à l’aide de la clause d’échappement ODBC CALL, Microsoft ?? SQL Server ??? pilote envoie la procédure à SQL Server en utilisant le mécanisme d’appel de procédure stockée distante. Les demandes RPC, qui contournent une grande partie de l'analyse des instructions et du traitement des paramètres dans SQL Server, sont plus rapides que l'instruction Transact-SQL EXECUTE.  
  
 Pour un exemple d’application qui illustre cette fonctionnalité, consultez [traiter des Codes de retour et les paramètres de sortie &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Pour exécuter une procédure en tant qu'appel RPC  
  
1.  Construisez une instruction SQL qui utilise la séquence d'échappement ODBC CALL. L'instruction utilise des marqueurs de paramètre pour chaque entrée, entrée/sortie et paramètre de sortie, et pour la valeur de retour de la procédure (le cas échéant) :  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Appelez [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) pour chaque paramètre d'entrée, d'entrée/sortie et de sortie et pour la valeur de retour de la procédure (le cas échéant).  
  
3.  Exécutez l'instruction avec [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Si une application soumet une procédure à l'aide de la syntaxe Transact-SQL EXECUTE (par opposition à la séquence d'échappement ODBC CALL), le pilote ODBC de SQL Server passe l'appel de procédure à SQL Server en tant qu'instruction SQL et non en tant qu'appel RPC. Par ailleurs, les paramètres de sortie ne sont pas retournés si l'instruction Transact-SQL EXECUTE est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Les rubriques de procédures de procédures stockées en cours d’exécution &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Traitement par lot des appels de procédure stockée](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Exécution de procédures stockées](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Appel d’une procédure stockée](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procédures](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
