---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 991757d1bfeae8ecc0dec3a69d82c3dcab6415b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914646"
---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|33129|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CANNOT_DISABLE_WIN_GROUP|  
|Texte du message|Impossible d'utiliser ALTER_LOGIN avec l'argument DISABLE pour refuser l'accès à un groupe Windows.|  
  
## <a name="explanation"></a>Explication  
 Ce message est généré lors d'une tentative de désactivation de la connexion d'un groupe Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La connexion d'un groupe Windows ne peut pas être désactivée. Pour supprimer temporairement l'autorisation d'accès accordée à un groupe Windows, révoquez avec REVOKE l'autorisation CONNECT de la connexion du groupe Windows. Les utilisateurs Windows peuvent encore bénéficier d'un accès par leur connexion individuelle ou via un autre groupe Windows. L'exemple suivant révoque l'autorisation de connexion au groupe de comptabilité Accounting du domaine WESTCOAST.  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
