---
title: MSSQLSERVER_823 | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a3889444fb2c605bccd36d30dbe324f220bbe942
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040888"
---
# <a name="mssqlserver823"></a>MSSQLSERVER_823
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|823|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|B_HARDERR|  
|Texte du message|Le système d'exploitation a retourné l'erreur %ls à SQL Server pendant une opération de %S_MSG au niveau du décalage %#016I64x dans le fichier '%ls'. D'autres messages peuvent fournir davantage d'informations dans le journal des erreurs SQL Server et le journal des événements système. Il s'agit d'une condition d'erreur sévère de niveau système qui met en péril l'intégrité de la base de données et qui doit être corrigée immédiatement. Effectuez une vérification complète de la cohérence de la base de données (DBCC CHECKDB). Cette erreur peut avoir de nombreuses causes ; pour plus d'informations, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Une demande de lecture ou d'écriture sous Windows a échoué. Le code d'erreur retourné par Windows et le texte correspondant sont intégrés au message. Dans le cas de la lecture, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a déjà retenté la demande quatre fois. Cette erreur résulte généralement d'un problème matériel, mais elle peut également provenir du pilote de périphérique. Pour plus d’informations sur l’erreur 823, consultez [http://support.microsoft.com/kb/828339](http://support.microsoft.com/kb/828339). Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S Microsoft SQL Server, chapitre 2](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cherchez des informations supplémentaires dans le journal des événements système. Contactez le fabricant du matériel ou le service clientèle et support technique de Microsoft pour déterminer la cause et l'action corrective à entreprendre. Une fois l'erreur matérielle corrigée, restaurez toutes les bases de données et exécutez DBCC CHECKDB.  
  
  