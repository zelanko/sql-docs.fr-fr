---
description: Create, méthode (ADOX)
title: Create, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
author: rothja
ms.author: jroth
ms.openlocfilehash: 588f73fcd2ced95be3cd7f8586faed864b38f8ad
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984840"
---
# <a name="create-method-adox"></a>Create, méthode (ADOX)
Crée un nouveau catalogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectString*  
 Valeur de **chaîne** utilisée pour se connecter à la source de données.  
  
## <a name="remarks"></a>Notes  
 La méthode **Create** crée et ouvre une nouvelle [connexion](../ado-api/connection-object-ado.md) ADO à la source de données spécifiée dans *connectString*. En cas de réussite, le nouvel objet de **connexion** est affecté à la propriété [ActiveConnection](./activeconnection-property-adox.md) .  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création de nouveaux catalogues.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Create, exemple de méthode (VB)](./create-method-example-vb.md)   
 [ActiveConnection, propriété (ADOX)](./activeconnection-property-adox.md)