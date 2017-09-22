---
title: '@@SERVERNAME (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 93d03e11df97075b2d608d7bfcc4e234c37971cd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40servername-transact-sql"></a>& #x 40 ; & #x 40 ; SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nom du serveur local qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar**  
  
## <a name="remarks"></a>Notes  
 Lors de l'installation, le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit le nom du serveur avec le nom de l'ordinateur. Pour modifier le nom du serveur, utilisez **sp_addserver**, puis redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées, @@SERVERNAME retourne des informations sur le nom du serveur local suivant si le nom du serveur local n’a pas été modifié depuis l’installation.  
  
|Instance|Informations sur le serveur|  
|--------------|------------------------|  
|Instance par défaut|'*nom_serveur*'|  
|Instance nommée|'*nom_serveur*\\*instancename*'|  
|instance de cluster de basculement - instance par défaut|'*nom_serveur_virtuel*'|  
|instance de cluster de basculement - instance nommée|'*nom_serveur_virtuel*\\*instancename*'|  
  
 Bien que le @@SERVERNAME fonction et la propriété SERVERNAME de la fonction SERVERPROPERTY puissent renvoyer des chaînes de mêmes formats, les informations peuvent être différents. La propriété SERVERNAME rapporte automatiquement les modifications apportées au nom réseau de l'ordinateur.  
  
 En revanche, @@SERVERNAME ne signale pas de telles modifications. @@SERVERNAME les modifications apportées au nom du serveur local en utilisant le **sp_addserver** ou **sp_dropserver** procédure stockée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'utilisation de `@@SERVERNAME`.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 Un exemple d'ensemble de résultats est présenté ci-dessous.  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de configuration &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  

