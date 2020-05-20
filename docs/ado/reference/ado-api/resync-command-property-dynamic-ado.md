---
title: Resync Command, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 916afef294a76e62702dbbd7cc413a0540484f62
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756479"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command, propriété dynamique (ADO)
Spécifie une chaîne de commande fournie par l’utilisateur que la méthode de [resynchronisation](../../../ado/reference/ado-api/resync-method.md) émet pour actualiser les données de la table nommée dans la propriété dynamique de la [table unique](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** qui est une chaîne de commande.  
  
## <a name="remarks"></a>Notes  
 L’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est le résultat d’une opération de jointure exécutée sur plusieurs tables de base. Les lignes affectées dépendent du paramètre *AffectRecords* de la méthode [Resync](../../../ado/reference/ado-api/resync-method.md) . La méthode de **resynchronisation** standard est exécutée si les propriétés de la table et de la **commande Resync** [uniques](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) ne sont pas définies.  
  
 La chaîne de commande de la propriété de **commande Resync** est une commande paramétrée ou une procédure stockée qui identifie de façon unique la ligne en cours d’actualisation, et retourne une ligne unique contenant le même nombre et l’ordre des colonnes que la ligne à actualiser. La chaîne de commande contient un paramètre pour chaque colonne de clé primaire dans la **table unique**; dans le cas contraire, une erreur d’exécution est retournée. Les paramètres sont automatiquement renseignés avec les valeurs de clé primaire de la ligne à actualiser.  
  
 Voici deux exemples basés sur SQL :  
  
 1 \) le **jeu d’enregistrements** est défini par une commande :  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 La propriété de la **commande Resync** est définie sur :  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 La **table unique** est *Orders* et sa clé primaire, *OrderID*, est paramétrable. La sous-sélection offre un moyen simple de vérifier par programmation que le même nombre et l’ordre des colonnes sont retournés comme par la commande d’origine.  
  
 2 \) le **Recordset** est défini par une procédure stockée :  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 La méthode **Resync** doit exécuter la procédure stockée suivante :  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 La propriété de la **commande Resync** est définie sur :  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Une fois encore, la **table unique** est *Orders* et sa clé primaire, *OrderID*, est paramétrable.  
  
 La **commande Resync** est une propriété dynamique ajoutée à la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) de l’objet **Recordset** lorsque la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
