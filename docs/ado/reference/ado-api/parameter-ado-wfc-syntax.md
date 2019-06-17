---
title: Paramètre (ADO - syntaxe WFC) | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: d39d181190d6bc28fa94271c7be787735e0515dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703975"
---
# <a name="parameter-ado---wfc-syntax"></a>Paramètre (ADO - syntaxe WFC)
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
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
  
### <a name="properties"></a>Properties  
  
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
 Le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet Obtient ou définit le contenu de cet objet. Le contenu est représenté en tant que VARIANT, un type d’objet qui peut avoir une valeur et plusieurs types de données.  
  
 ADO/WFC implémente la **valeur** propriété avec le **getValue** (méthode), qui retourne un objet de type VARIANT ; et le **setValue** (méthode), qui prend une variante en tant qu’argument. Variantes sont très efficaces dans certains langages, tels que Microsoft Visual Basic.  
  
 Outre le **valeur** propriété, ADO/WFC fournit *accesseur* les méthodes qui utilisent des types de données Java pour obtenir et définir le contenu de **paramètre** objets. La plupart de ces méthodes ont des noms au format **obtenir**_DataType_ ou **définir**_DataType_.  
  
 Il existe une exception notable : Il existe aucune **getNull** propriété ; au lieu de cela, il existe un **isNull** propriété qui retourne une valeur booléenne indiquant si le champ est null.  
  
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
 [Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)
