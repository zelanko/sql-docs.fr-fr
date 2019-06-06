---
title: Append, méthode (procédures ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1c379826b16ef805abfedb0467d3385010ca1b99
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66708584"
---
# <a name="append-method-adox-procedures"></a>Append, méthode (procédures ADOX)
Ajoute un nouveau [procédure](../../../ado/reference/adox-api/procedure-object-adox.md) de l’objet à la [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Un **chaîne** valeur qui spécifie le nom de la procédure pour créer et à ajouter.  
  
 *Commande*  
 ADO [commande](../../../ado/reference/ado-api/command-object-ado.md) objet qui représente la procédure pour créer et à ajouter.  
  
## <a name="remarks"></a>Notes  
 Crée une procédure dans la source de données avec le nom et les attributs spécifiés dans le **commande** objet.  
  
 Si le texte de commande qui spécifie l’utilisateur représente une vue plutôt qu’une procédure, le comportement dépend du fournisseur utilisé. **Ajouter** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
> [!NOTE]
>  Lorsque vous utilisez le fournisseur OLE DB pour Microsoft Jet, le **procédures** collection **Append** méthode vous permettra de spécifier un **vue** au lieu d’un  **Procédure** dans le *commande* paramètre. Le **vue** sera ajouté à la source de données et sera ajouté à la **procédures** collection. Après le **Append**, si le **procédures** et **vues** collections sont actualisées, les **vue** ne sera plus dans le **Procédures** collection et apparaîtra dans le **vues** collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procedures Append, méthode-exemple (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append, méthode (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append, méthode (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
