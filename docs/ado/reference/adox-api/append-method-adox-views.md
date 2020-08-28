---
description: Append, méthode (vues ADOX)
title: Append, méthode (vues ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 77682d479d65c7ccc0dd01fd1fd86627a580d8c5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985390"
---
# <a name="append-method-adox-views"></a>Append, méthode (vues ADOX)
Crée un objet de [vue](./view-object-adox.md) et l’ajoute à la collection [views](./views-collection-adox.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Valeur de **chaîne** qui spécifie le nom de la vue à créer.  
  
 *Commande*  
 Objet de [commande](../ado-api/command-object-ado.md) ADO qui représente la vue à créer.  
  
## <a name="remarks"></a>Notes  
 Crée une vue dans la source de données avec le nom et les attributs spécifiés dans l’objet **Command** .  
  
 Si le texte de la commande que l’utilisateur spécifie représente une procédure plutôt qu’une vue, le comportement dépend du fournisseur. L' **Ajout** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
> [!NOTE]
>  Lorsque vous utilisez le fournisseur de OLE DB pour Microsoft Jet, la méthode d' **Ajout** de la collection **views** vous permet de spécifier une **procédure** plutôt qu’une **vue** dans le paramètre *Command* . La **procédure** sera ajoutée à la source de données et sera ajoutée à la collection **views** . Après l' **Ajout**, si les collections **procedures** et **views** sont actualisées, la **procédure** ne figurera plus dans la collection **views** et apparaîtra dans la collection **procedures** .  
  
## <a name="applies-to"></a>S'applique à  
 [Views, collection (ADOX)](./views-collection-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Views, exemple de méthode Append (VB)](./views-append-method-example-vb.md)   
 [Append, méthode (colonnes ADOX)](./append-method-adox-columns.md)   
 [Append, méthode (groupes ADOX)](./append-method-adox-groups.md)   
 [Append, méthode (Index ADOX)](./append-method-adox-indexes.md)   
 [Append, méthode (clés ADOX)](./append-method-adox-keys.md)   
 [Append, méthode (procédures ADOX)](./append-method-adox-procedures.md)   
 [Append, méthode (Tables ADOX)](./append-method-adox-tables.md)   
 [Append, méthode (utilisateurs ADOX)](./append-method-adox-users.md)