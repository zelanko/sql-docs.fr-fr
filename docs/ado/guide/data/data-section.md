---
title: Section de données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 76cd14b8ee1c5a55e0312993090bfaf098c7e219
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702137"
---
# <a name="data-section"></a>Section de données
La section de données définit les données de l’ensemble de lignes ainsi que tout en attente de mises à jour, les insertions ou les suppressions. La section de données peut contenir zéro ou plusieurs lignes. Il ne peut contenir que des données à partir d’un ensemble de lignes où la ligne est définie par le schéma. En outre, comme mentionné précédemment, les colonnes sans aucune donnée peuvent être omis. Si un attribut ou un sous-élément est utilisé dans la section de données et que cette construction n’a pas été définie dans la section de schéma, il est ignoré en mode silencieux.  
  
## <a name="string"></a>String  
 Les caractères XML réservés dans les données texte doivent être remplacées par des entités de caractères approprié. Par exemple, dans le nom de la société « Jean Garage », le guillemet simple doit être remplacé par une entité. La ligne réelle peut se présenter comme suit :  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 Les caractères suivants sont réservés dans XML et doivent être remplacées par des entités de caractères : {', », &,\<, >}.  
  
## <a name="binary"></a>Binaire  
 Données binaires sont bin.hex encodé (autrement dit, un octet correspond à deux caractères, un caractère par quartet).  
  
## <a name="datetime"></a>DateTime  
 Le format VT_DATE variant n’est pas directement pris en charge par les types de données XML-Data. Le format correct pour les dates avec le composant à la fois une date et l’heure est aaaa-mm-jjThh.  
  
 Pour plus d’informations sur les formats de date spécifiée par XML, consultez le [spécification W3C XML-Data](https://go.microsoft.com/fwlink/?LinkId=5692).  
  
 Lorsque la spécification XML-Data définit deux types de données équivalents (par exemple, i4 == int), ADO sera écrit le nom convivial, mais elle est lue dans les deux.  
  
## <a name="managing-pending-changes"></a>La gestion des modifications en attente  
 Un jeu d’enregistrements peut être ouverts dans l’immédiat ou mode de mise à jour par lot. Lorsqu’ils sont ouverts en mode de mise à jour par lot avec des curseurs côté client, toutes les modifications apportées à l’objet Recordset sont en état d’attente jusqu'à ce que la méthode UpdateBatch est appelée. Modifications en attente sont également conservées lorsque le jeu d’enregistrements est enregistré. Dans XML, ils sont représentés par l’utilisation des éléments « update » défini dans l’urn : schemas-microsoft-rowset. En outre, si un ensemble de lignes peut être mis à jour, la propriété être mise à jour doit être définie true dans la définition de la ligne. Par exemple, pour définir que la table Shippers contient des modifications en attente, la définition de ligne aurait coup de œil se présenter comme suit.  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 Cela indique à la persistance au fournisseur de données afin qu’ADO puisse créer un objet Recordset modifiable.  
  
 Les données d’exemple suivant montrent l’aspect des insertions, suppressions et les modifications dans le fichier persistant.  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 Une mise à jour contienne toujours les données de ligne d’origine entier suivies par les données de la ligne modifiée. La ligne modifiée peut contenir toutes les colonnes ou uniquement les colonnes qui ont été modifiées. Dans l’exemple précédent, la ligne 2 de l’expéditeur n’est pas modifiée, et uniquement la colonne Phone les valeurs ont changé pour Shipper 3 et est donc la seule colonne incluse dans la ligne modifiée. Les lignes insérées pour Shipper 12, 13 et 14 sont traités par lot balise rs : insert dans un seul ensemble. Notez que les lignes supprimées peuvent également être regroupés, bien que cela n’est pas présenté dans l’exemple précédent.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
