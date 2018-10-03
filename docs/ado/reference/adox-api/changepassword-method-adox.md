---
title: ChangePassword, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96268fac4b81230fcb63db6b48ef4ef794abb9c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788707"
---
# <a name="changepassword-method-adox"></a>ChangePassword, méthode (ADOX)
Modifie le mot de passe pour un [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) compte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>Paramètres  
 *OldPassword*  
 Un **chaîne** valeur qui spécifie le mot de passe existant. Si l’utilisateur ne dispose actuellement d’un mot de passe, utilisez une chaîne vide (" ») pour *OldPassword*.  
  
 *NewPassword*  
 Un **chaîne** valeur qui spécifie le nouveau mot de passe.  
  
## <a name="remarks"></a>Notes  
 Pour des raisons de sécurité, l’ancien mot de passe doit être spécifié en plus du nouveau mot de passe.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge l’administration des propriétés de tiers de confiance.  
  
## <a name="applies-to"></a>S'applique à  
 [User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Append (méthode) sur les collections Groups et Users, ChangePassword, exemple de méthodes (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)
