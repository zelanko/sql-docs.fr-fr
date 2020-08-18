---
description: MSSQLSERVER_10003
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d25d4a203c5871c4d9542c03e3872dd1206bb543
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339635"
---
# <a name="mssqlserver_10003"></a>MSSQLSERVER_10003
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|10003|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HR_E_OUTOFMEMORY|  
|Texte du message|Le fournisseur n'a plus de mémoire.|  
  
## <a name="explanation"></a>Explication  
L'insuffisance de mémoire système a provoqué une pénurie de mémoire pour le fournisseur OLE DB.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Redémarrez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cela ne change rien, redémarrez l'ordinateur. Si le problème persiste, collectez les événements de trace OLE DB à l’aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et fournissez ces données au support technique du fournisseur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
[Modèles et autorisations du générateur de SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
