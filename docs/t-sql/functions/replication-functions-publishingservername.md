---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 56c0ccb2379869358fd3470fe5e365a6e6ce5b75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767847"
---
# <a name="replication-functions---publishingservername"></a>Fonctions de réplication - PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le nom du serveur de publication d'origine d'une base de données publiée qui participe à une session de mise en miroir de bases de données. Cette fonction est exécutée sur une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'un éditeur d'une base de données de publication. Utilisez-la pour déterminer l'éditeur d'origine de la base de données publiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar**  
  
## <a name="remarks"></a>Notes   
 PUBLISHINGSERVERNAME est utilisée dans tous les types de réplication.  
  
 PUBLISHINGSERVERNAME s'utilise lorsqu'une session de mise en miroir d'une base de données existe sur la base de données de publication entre l'éditeur et l'instance d'un partenaire de mise en miroir.  
  
 Cette fonction doit être exécutée dans le contexte d'une base de données de publication. Lorsque PUBLISHINGSERVERNAME est exécutée sur une base de données de publication de l'instance du serveur miroir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nom de l'instance de l'éditeur originaire de la base de données publiée est renvoyé. Lorsque cette fonction est exécutée sur une base de données de l'instance du serveur miroir qui n'est pas publiée ou qui est publiée à partir de l'instance du serveur miroir après un basculement, le nom de l'instance du serveur miroir est renvoyé. Lorsque cette fonction est exécutée sur l'instance de l'éditeur d'origine, le nom de l'éditeur est renvoyé.  
  
## <a name="see-also"></a> Voir aussi  
 [Mise en miroir de bases de données et réplication &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [Fonctions de réplication &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
