---
title: À l’aide de curseurs de serveur | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 689df4a5d8201fa6f7f59ead9ce87de01e0cd705
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142479"
---
# <a name="using-server-cursors"></a>Utilisation des curseurs côté serveur
  Si une application ODBC définit des attributs de curseur ODBC que les valeurs par défaut, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client demande au serveur d’implémenter un curseur de serveur API du même type. L'utilisation de curseurs côté serveur d'API libère la mémoire sur le client et peut réduire considérablement le trafic réseau entre le client et le serveur.  
  
 Un inconvénient possible des curseurs côté serveur d'API est qu'ils ne prennent pas en charge toutes les instructions SQL. Les curseurs côté serveur d'API ne peuvent pas être utilisés pour exécuter :  
  
-   Les lots ou les procédures stockées qui retournent plusieurs ensembles de résultats.  
  
-   Les instructions SELECT contenant les clauses COMPUTE, COMPUTE BY, FOR BROWSE ou INTO.  
  
-   Une instruction EXECUTE faisant référence à une procédure stockée distante.  
  
 En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'exécution d'une instruction avec ces caractéristiques à l'aide d'un curseur côté serveur provoque la conversion du curseur en un jeu de résultats par défaut. En cas de connexion aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il s'ensuit une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](how-cursors-are-implemented.md)  
  
  