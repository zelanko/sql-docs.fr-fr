---
title: Commande (ADO - syntaxe WFC) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Command collection [ADO], ADO/WFC syntax
ms.assetid: 39d0aa06-03ac-4c9a-8400-83947756ef99
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4722316cc92567000294c57089afd8840bea1bcd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919828"
---
# <a name="command-ado---wfc-syntax"></a>Command (ADO - syntaxe WFC)
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="constructor"></a>Constructeur  
  
```  
public Command()  
public Command(String commandtext)  
```  
  
### <a name="methods"></a>Méthodes  
  
```  
public void cancel()  
public com.ms.wfc.data.Parameter createParameter(String  
    Name, int Type, int Direction, int Size, Object Value)  
public Recordset execute()  
public Recordset execute(Object[] parameters)  
public Recordset execute(Object[] parameters, int options)  
public int executeUpdate(Object[] parameters)  
public int executeUpdate(Object[] parameters, int options)  
public int executeUpdate()  
```  
  
 Le **executeUpdate** méthode est une méthode spéciale qui appelle le ADO sous-jacent **exécuter** méthode avec certains paramètres. Le **executeUpdate** méthode ne prend pas en charge le retour d’un **Recordset** objet, donc le **exécuter** la méthode *options* paramètre est modifié avec **AdoEnums.ExecuteOptions.NORECORDS**. Après le **exécuter** méthode se termine, sa mise à jour *RecordsAffected* paramètre est passé à la **executeUpdate** (méthode), qui retourne finalement un **int**.  
  
### <a name="properties"></a>Properties  
  
```  
public com.ms.wfc.data.Connection getActiveConnection()  
public void setActiveConnection(com.ms.wfc.data.Connection con)  
public void setActiveConnection(String conString)  
public String getCommandText()  
public void setCommandText(String command)  
public int getCommandTimeout()  
public void setCommandTimeout(int timeout)  
public int getCommandType()  
public void setCommandType(int type)  
public String getName()  
public void setName(String name)  
public boolean getPrepared()  
public void setPrepared(boolean prepared)  
public int getState()  
public com.ms.wfc.data.Parameter getParameter(int n)  
public com.ms.wfc.data.Parameter getParameter(String n)  
public com.ms.wfc.data.Parameters getParameters()  
public AdoProperties getProperties()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
