---
title: Parameter (syntaxe ADO-WFC) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22f9d928cf008396346067a3e166fa281be4093d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931713"
---
# <a name="parameter-ado---wfc-syntax"></a>Paramètre (ADO - syntaxe WFC)
## <a name="package-commswfcdata"></a>package com. ms. wfc. Data  
  
### <a name="constructor"></a>Constructeur  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>Méthodes  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>Méthodes d’accesseur de paramètre  
 La propriété [value](../../../ado/reference/ado-api/value-property-ado.md) d’un objet [Parameter](../../../ado/reference/ado-api/parameter-object.md) obtient ou définit le contenu de cet objet. Le contenu est représenté sous la forme d’une variante, d’un type d’objet auquel une valeur et l’un des différents types de données peuvent être attribués.  
  
 ADO/WFC implémente la propriété **value** avec la méthode **GetValue** , qui retourne un objet variant ; et la méthode **SetValue** , qui prend une variante comme argument. Les VARIANTEs sont très efficaces dans certains langages, tels que Microsoft Visual Basic.  
  
 En plus de la propriété **value** , ADO/WFC fournit des méthodes d' *accesseur* qui utilisent des types de données Java pour récupérer et définir le contenu des objets **Parameter** . La plupart de ces méthodes ont des noms au format **obtenir**le_type de données_ ou **définir**le type de_données_.  
  
 Il y a une exception notable : il n’existe aucune propriété **getNull** ; au lieu de cela, il existe une propriété **IsNull** qui retourne une valeur booléenne indiquant si le champ est null.  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)
