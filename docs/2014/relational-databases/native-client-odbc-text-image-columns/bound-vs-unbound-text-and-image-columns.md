---
title: Lié à Visual Studio. Détachées des colonnes Text et Image | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d77a71aae13c9601acc0ba56146e7882e6ee6e7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430628"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Lié à Visual Studio. Indépendant colonnes Text et Image
  Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données pour indépendant **texte**, **ntext**, ou **image** colonnes au niveau de la temps **SQLFetch** est effectuée. Le **texte**, **ntext**, ou **image** données ne sont pas réellement récupérées à partir du serveur jusqu'à ce que les problèmes des applications [SQLGetData](../native-client-odbc-api/sqlgetdata.md) pour le colonne.  
  
 De nombreuses applications peuvent être écrites afin qu’aucun **texte**, **ntext**, ou **image** données s’affiche pendant un utilisateur est simplement le défilement haut et le bas dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut ensuite appeler **SQLGetData** pour récupérer le **texte**, **ntext**, ou **image** données. Cela évite de transmettre le **texte**, **ntext**, ou **image** données pour toutes les lignes de l’utilisateur sans sélectionner et peut par conséquent d’empêchent la transmission de très grande taille quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des colonnes Text et Image](managing-text-and-image-columns.md)   
 [Comportements des curseurs](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
