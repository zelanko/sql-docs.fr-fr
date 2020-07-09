---
title: MSSQLSERVER_7988 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be9326ff03ac3ec8550c71e03c4889bd4492652e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767871"
---
# <a name="mssqlserver_7988"></a>MSSQLSERVER_7988
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|7988|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED|  
|Texte du message|Pré-vérifications de table système : ID d’objet O_ID. Boucle dans la chaîne des données détectée à P_ID. Vérifiez l'instruction qui s'est arrêtée en raison d'une erreur irréparable.|  
  
## <a name="explanation"></a>Explication  
La première étape d'un DBCC CHECKDB consiste à effectuer des prévérifications sur les pages de données des tables système critiques. Toute erreur détectée à ce stade étant irréparable, DBCC CHECKDB s’arrête immédiatement. Une boucle de liaison de page a été détectée dans la page *P_ID*. Cela se produit lorsque les pointeurs d'une page menant à la page suivante finissent par revenir à cette page.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et des applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, ainsi que le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
Si le problème n'est pas matériel et si une restauration réputée en bon état est disponible, restaurez la base de données à partir de la sauvegarde.  
  
### <a name="run-dbcc-checkdb"></a>Exécuter DBCC CHECKDB  
Non applicable. Cette erreur ne peut pas être réparée automatiquement. Si vous ne pouvez pas restaurer la base de données à partir d'une sauvegarde, contactez le service de support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
