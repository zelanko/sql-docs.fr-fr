---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4a7ee12d9462c8772c0e005c76d5dd12445b99a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727513"
---
# <a name="mssqlserver_8443"></a>MSSQLSERVER_8443
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|8443|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB_DIALOG_WO_CONV_GROUP|  
|Texte du message|La conversation avec l’ID '%.*ls' et l’initiateur %d fait référence à un groupe de conversations manquant '%.\*ls'. Exécutez DBCC CHECKDB pour analyser et réparer la base de données.|  
  
## <a name="explanation"></a>Explication  
La couche de métadonnées a retourné la valeur NULL pour le groupe de conversations. La base de données a été endommagée d'une certaine façon. Une erreur de disque est une source d'endommagement possible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC CHECKDB en mode réparation pour ramener la base de données à un état cohérent. Cela peut entraîner la suppression de messages si cela s'avère nécessaire pour restaurer la cohérence. Examinez les journaux des erreurs du système pour voir si cette erreur a été causée par une autre défaillance dans le système.  
  
