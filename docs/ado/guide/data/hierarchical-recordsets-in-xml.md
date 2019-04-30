---
title: Recordsets hiérarchiques dans XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], in XML
ms.assetid: 5d4b11c4-c94f-4910-b99b-5b9abc50d791
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 860732a8d694ee59dae05f76eb9cabe49ebc8c96
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161573"
---
# <a name="hierarchical-recordsets-in-xml"></a>Recordsets hiérarchiques dans XML
ADO autorise la persistance d’objets Recordset hiérarchiques dans XML. Avec de tels objets, la valeur d’un champ dans le jeu d’enregistrements parent est un autre jeu d’enregistrements. Ces champs sont représentés en tant qu’éléments enfants dans le flux XML plutôt que d’un attribut.  
  
## <a name="remarks"></a>Notes  
 L’exemple suivant illustre ce cas :  
  
```  
Rs.Open "SHAPE {select stor_id, stor_name, state from stores} APPEND ({select stor_id, ord_num, ord_date, qty from sales} AS rsSales RELATE stor_id TO stor_id)", "Provider=MSDataShape;DSN=pubs;Integrated Security=SSPI;"  
```  
  
 Voici le format XML de l’objet Recordset persistante :  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"     xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"     xmlns:rs="urn:schemas-microsoft-com:rowset"   
    xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="stor_id" rs:number="1"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="4"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="stor_name" rs:number="2" rs:nullable="true"   
        rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="40"/>   
      </s:AttributeType>   
      <s:AttributeType name="state" rs:number="3" rs:nullable="true"   
        rs:writeunknown="true">   
        <s:datatype dt:type="string" dt:maxLength="2"   
          rs:fixedlength="true"/>   
      </s:AttributeType>   
      <s:ElementType name="rsSales" content="eltOnly"   
        rs:updatable="true" rs:relation="010000000100000000000000">   
        <s:AttributeType name="stor_id" rs:number="1"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="4"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_num" rs:number="2"   
          rs:writeunknown="true">   
          <s:datatype dt:type="string" dt:maxLength="20"   
            rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="ord_date" rs:number="3"   
          rs:writeunknown="true">   
            <s:datatype dt:type="dateTime" dt:maxLength="16"   
              rs:scale="3" rs:precision="23" rs:fixedlength="true"   
              rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:AttributeType name="qty" rs:number="4" rs:writeunknown="true">   
          <s:datatype dt:type="i2" dt:maxLength="2" rs:precision="5"   
            rs:fixedlength="true" rs:maybenull="false"/>   
        </s:AttributeType>   
        <s:extends type="rs:rowbase"/>   
      </s:ElementType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  <rs:data>   
    <z:row stor_id="6380" stor_name="Eric the Read Books" state="WA">   
      <rsSales stor_id="6380" ord_num="6871"   
        ord_date="1994-09-14T00:00:00" qty="5"/>   
      <rsSales stor_id="6380" ord_num="722a"   
        ord_date="1994-09-13T00:00:00" qty="3"/>   
    </z:row>   
    <z:row stor_id="7066" stor_name="Barnum's" state="CA">   
      <rsSales stor_id="7066" ord_num="A2976"   
        ord_date="1993-05-24T00:00:00" qty="50"/>   
      <rsSales stor_id="7066" ord_num="QA7442.3"   
        ord_date="1994-09-13T00:00:00" qty="75"/>   
    </z:row>   
    <z:row stor_id="7067" stor_name="News & Brews" state="CA">   
      <rsSales stor_id="7067" ord_num="D4482"   
        ord_date="1994-09-14T00:00:00" qty="10"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="40"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
      <rsSales stor_id="7067" ord_num="P2121"   
        ord_date="1992-06-15T00:00:00" qty="20"/>   
    </z:row>   
  </rs:data>   
</xml>   
```  
  
 L’ordre exact des colonnes dans le jeu d’enregistrements parent n’est pas évident lorsqu’il est conservé de cette manière. N’importe quel champ de la page parente peut contenir un objet Recordset. Le fournisseur de persistance conserve toutes les colonnes scalaires tout d’abord en tant qu’attributs, puis toutes les « colonnes » du jeu d’enregistrements enfant en tant qu’éléments enfants de la ligne parente. La position ordinale du champ dans le parent du jeu d’enregistrements peut être obtenu en examinant la définition de schéma de l’objet Recordset. Chaque champ a une propriété OLE DB, rs : number, définie dans l’espace de noms du schéma Recordset qui contient le nombre ordinal de ce champ.  
  
 Les noms de tous les champs dans le jeu d’enregistrements enfant sont concaténés avec le nom du champ dans le jeu d’enregistrements qui contient cet enfant du parent. Il s’agit pour vous assurer qu’il n’y a aucune collisions de noms dans les cas où le parent et enfant Recordsets les deux contiennent un champ qui est obtenu à partir de deux tables différentes mais portant le même nom.  
  
 Lors de l’enregistrement des Recordsets hiérarchiques en XML, vous devez connaître les restrictions suivantes dans ADO :  
  
-   Un objet Recordset hiérarchique avec en attente de mises à jour ne peut pas être conservé au format XML.  
  
-   Un jeu d’enregistrements hiérarchique créé avec une commande de mise en forme paramétrée ne peut pas être persistante (au format XML ou ADTG).  
  
-   ADO enregistre actuellement la relation entre le parent et les jeux d’enregistrements enfants sous la forme d’un objet binaire volumineux (BLOB). Les balises XML pour décrire cette relation n’ont pas encore été définies dans l’espace de noms de schéma d’ensemble de lignes.  
  
-   Lors de l’enregistrée d’un objet Recordset hiérarchique, enfant de tous les jeux d’enregistrements est enregistrés en même temps. Si le jeu d’enregistrements actuel est un enfant d’un autre jeu d’enregistrements, son parent n’est pas enregistré. Jeux d’enregistrements qui forment la sous-arborescence de l’ensemble d’enregistrements actuel de tous les enfants est enregistrés.  
  
 Quand un objet Recordset hiérarchique est rouvert à partir de son format de persistance XML, vous devez être conscient des limitations suivantes :  
  
-   Si l’enregistrement enfant contient des enregistrements pour lesquels il n’existe aucun enregistrement parent correspondant, ces lignes ne sont pas écrites dans la représentation XML de l’objet Recordset hiérarchique. Par conséquent, ces lignes seront perdues lorsque le Recordset est rouvert à partir de son emplacement de persistance.  
  
-   Si un enregistrement enfant est lié à plusieurs enregistrements de parent, puis rouvrir le jeu d’enregistrements, le jeu d’enregistrements enfants peut contenir des enregistrements en double. Toutefois, ces doublons sera uniquement visibles si l’utilisateur travaille directement avec l’ensemble de lignes enfant sous-jacent. Si un chapitre est utilisé pour naviguer de l’objet Recordset (qui est la seule façon de naviguer dans ADO), les doublons ne sont pas visibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
