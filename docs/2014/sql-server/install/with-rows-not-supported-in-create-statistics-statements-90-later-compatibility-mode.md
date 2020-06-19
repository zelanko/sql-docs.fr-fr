---
title: WITH ROWS n’est pas pris en charge dans les instructions CREATe STATISTICs dans le mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065050"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>La clause WITH ROWS n'est pas prise en charge dans les instructions CREATE STATISTICS en mode de compatibilité 90 ou ultérieur
  La spécification de la clause WITH ROWS dans les instructions CREATE STATISTICS n'est pas prise en charge lorsque vous exécutez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de compatibilité 90 ou ultérieur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez les instructions CREATe STATISTICs qui incluent WITH ROWS en spécifiant WITH SAMPLE *Number* Rows, ou en spécifiant d’autres options conformes à la syntaxe documentée. Pour plus d’informations, consultez la rubrique «CREATe STATISTICs (Transact-SQL) dans Documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
