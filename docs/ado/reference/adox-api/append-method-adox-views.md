---
title: "Append (méthode) (vues ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 535f25f475f6357d467e2f7ac19a96ed6eea1605
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-views"></a>Append (méthode) (vues ADOX)
Crée un nouveau [vue](../../../ado/reference/adox-api/view-object-adox.md) de l’objet et l’ajoute à la [vues](../../../ado/reference/adox-api/views-collection-adox.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 A **chaîne** valeur qui spécifie le nom de la vue à créer.  
  
 *Command*  
 ADO [commande](../../../ado/reference/ado-api/command-object-ado.md) objet qui représente la vue à créer.  
  
## <a name="remarks"></a>Notes  
 Crée une nouvelle vue de source de données avec le nom et les attributs spécifiés dans le **commande** objet.  
  
 Si le texte de commande par l’utilisateur représente une procédure plutôt qu’une vue, le comportement dépend du fournisseur. **Ajouter** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
> [!NOTE]
>  Lorsque vous utilisez le fournisseur OLE DB pour Microsoft Jet, le **vues** collection **Append** méthode vous permettra de spécifier un **procédure** plutôt qu’un **vue** dans les *commande* paramètre. Le **procédure** sera ajouté à la source de données et est ajoutée à la **vues** collection. Après le **Append**, si le **procédures** et **vues** collections sont actualisées, les **procédure** ne pourra plus être dans le **vues** collection et apparaîtra dans le **procédures** collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Collection de vues (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Views Append, méthode-exemple (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append (méthode) (colonnes ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (méthode) (groupes ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (méthode) (Index ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (méthode) (clés ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (méthode) (procédures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (méthode) (Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (méthode) (utilisateurs ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
