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
manager: craigg
ms.openlocfilehash: 164d71a333c09b076a6e292aa8cd2aeeb3ff464d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765993"
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8443|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB_DIALOG_WO_CONV_GROUP|  
|Texte du message|La conversation avec l’ID '%.*ls' et l’initiateur %d fait référence à un groupe de conversations manquant '%.\*ls'. Exécutez DBCC CHECKDB pour analyser et réparer la base de données.|  
  
## <a name="explanation"></a>Explication  
La couche de métadonnées a retourné la valeur NULL pour le groupe de conversations. La base de données a été endommagée d'une certaine façon. Une erreur de disque est une source d'endommagement possible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC CHECKDB en mode réparation pour ramener la base de données à un état cohérent. Cela peut entraîner la suppression de messages si cela s'avère nécessaire pour restaurer la cohérence. Examinez les journaux des erreurs du système pour voir si cette erreur a été causée par une autre défaillance dans le système.  
  
