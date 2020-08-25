---
description: Append, méthode (procédures ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f416d8223e828d724f1eabbe4ab82061204af0f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771408"
---
# <a name="append-method-adox-procedures"></a>Append, méthode (procédures ADOX)
Ajoute un nouvel objet de [procédure](./procedure-object-adox.md) à la collection [procedures](./procedures-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Valeur de **chaîne** qui spécifie le nom de la procédure à créer et à ajouter.  
  
 *Commande*  
 Objet de [commande](../ado-api/command-object-ado.md) ADO qui représente la procédure à créer et à ajouter.  
  
## <a name="remarks"></a>Notes  
 Crée une nouvelle procédure dans la source de données avec le nom et les attributs spécifiés dans l’objet **Command** .  
  
 Si le texte de la commande que l’utilisateur spécifie représente une vue plutôt qu’une procédure, le comportement dépend du fournisseur utilisé. L' **Ajout** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
> [!NOTE]
>  Lorsque vous utilisez le fournisseur de OLE DB pour Microsoft Jet, la méthode **Append** de la collection **procedures** vous permet de spécifier une **vue** plutôt qu’une **procédure** dans le paramètre *Command* . La **vue** sera ajoutée à la source de données et sera ajoutée à la collection **procedures** . Après l' **Ajout**, si les collections **procedures** et **views** sont actualisées, la **vue** ne figurera plus dans la collection **procedures** et apparaîtra dans la collection **views** .  
  
## <a name="applies-to"></a>S'applique à  
 [Procedures, collection (ADOX)](./procedures-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procedures, exemple de méthode Append (VB)](./procedures-append-method-example-vb.md)   
 [Append, méthode (colonnes ADOX)](./append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](./append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](./append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](./append-method-adox-keys.md)   
 [Append, méthode (Tables ADOX)](./append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](./append-method-adox-users.md)   
 [Append, méthode (vues ADOX)](./append-method-adox-views.md)