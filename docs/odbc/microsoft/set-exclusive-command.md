---
title: SET EXCLUSIVE Commande (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d140c4be3ab850547ac82f9b954e7313b008dbf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300859"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE, commande
Précise si les fichiers de table sont ouverts pour une utilisation exclusive ou partagée sur un réseau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Limite l’accessibilité d’une table ouverte sur un réseau à l’utilisateur qui l’a ouvert. La table n’est pas accessible aux autres utilisateurs du réseau. SET EXCLUSIVE ON empêche également tous les autres utilisateurs d’avoir un accès sans lecture seulement.  
  
 OFF  
 (Défaut pour le pilote; les défauts de Visual FoxPro sont ON pour la session de données mondiale et OFF pour une session de données privées.) Permet de partager et de modifier une table ouverte sur un réseau par n’importe quel utilisateur du réseau.  
  
## <a name="remarks"></a>Notes  
 Changer le paramètre de SET EXCLUSIVE ne change pas l’état des tables précédemment ouvertes. Par exemple, si une table est ouverte avec SET EXCLUSIVE réglé sur ON et SET EXCLUSIVE est ensuite changé en OFF, la table conserve son statut d’usage exclusif.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’ODBC pour Visual FoxPro, boîte de dialogue](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
