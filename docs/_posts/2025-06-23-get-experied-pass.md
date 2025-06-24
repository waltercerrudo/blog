---
title: Fecha de vencimiento de contraseña de usuarios AD
description: Guía para trabajar con jekyll y publicar artículos.
author: wcerrudo
layout: default
grand_parent: Layout
date: 2025-06-23 11:33:00 +0800
categories: [snipets]
tags: [bat, ad]
---

Snippet para obtener la fecha de expiración de cuentas de AD

Creamos un archivo llamado getExpireDate.ps1

```powershell
<# listados de usurios sobre los cuales consultar #>
$usuarios = @( "usuario1", "usuario2")

# Ancho fijo para columnas
$anchoUsuario = 15
$anchoFecha   = 20

foreach ($u in $usuarios) {
    $lineas = net user $u /domain
    $expira = $lineas | Where-Object { $_ -like "*La contrase*a expira*" }

    $usuarioFormateado = $u.PadRight($anchoUsuario)

    if ($expira) {
        if ($expira -match "\d{2}/\d{2}/\d{4} \d{1,2}:\d{2}:\d{2}") {
            $fecha = $matches[0].PadLeft($anchoFecha)
        } else {
            $fecha = "Fecha no reconocida".PadLeft($anchoFecha)
        }
    } else {
        $fecha = "No encontrada".PadLeft($anchoFecha)
    }

    Write-Output "$usuarioFormateado$fecha"
}
```
Lo invocamos desde la linea de comandos

```bat 
.\getExpireDate.ps1 > .\resultado.txt
```

Siendo resultado un archivo de texto de la siguiente forma

```text
usuario1          26/07/2025 8:26:10
usuario2        18/08/2025 7:47:29
```