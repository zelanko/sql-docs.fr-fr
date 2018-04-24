---
title: Append (méthode) (procédures ADOX) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a0974d3b6de9b1f8abfe61d9883aa60a4326c0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="append-method-adox-procedures"></a>Append (méthode) (procédures ADOX)
Ajoute un nouveau [procédure](../../../ado/reference/adox-api/procedure-object-adox.md) de l’objet à la [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 A **chaîne** valeur qui spécifie le nom de la procédure pour créer et à ajouter.  
  
 *Command*  
 ADO [commande](../../../ado/reference/ado-api/command-object-ado.md) objet qui représente la procédure à créer et à ajouter.  
  
## <a name="remarks"></a>Notes  
 Crée une procédure dans la source de données avec le nom et les attributs spécifiés dans le **commande** objet.  
  
 Si le texte de commande par l’utilisateur représente une vue, plutôt qu’une procédure, le comportement dépend du fournisseur utilisé. **Ajouter** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
> [!NOTE]
>  Lorsque vous utilisez le fournisseur OLE DB pour Microsoft Jet, le **procédures** collection **Append** méthode vous permettra de spécifier un **vue** plutôt qu’un **procédure** dans les *commande* paramètre. Le **vue** sera ajouté à la source de données et est ajoutée à la **procédures** collection. Après le **Append**, si le **procédures** et **vues** collections sont actualisées, les **vue** ne pourra plus être dans le **procédures** collection et apparaîtra dans le **vues** collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures ajouter l’exemple de méthode (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append (méthode) (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (méthode) (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (méthode) (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (méthode) (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
