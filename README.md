# /**
 * PROJECT: ULTRA INJECTOR V16 - GOD MODE
 * HOSTED: https://ruizbere491-netizen.github.io/Scripss_FF_V/
 * OPTIMIZED FOR: iPhone 15 Pro Max (A17 Pro Chip)
 */

async function onResponse(request, response) {
    let body = response.body;
    const url = request.url;

    // 1. BYPASS DE SEGURIDAD (Evita detección de Garena)
    if (url.includes("report") || url.includes("log") || url.includes("geotrust")) {
        return response;
    }

    // 2. INYECCIÓN DE PODER (M1014 & ARMAS DE IMPACTO)
    if (url.includes("com.dts.freefire") || url.includes("battle_config") || url.includes("weapon")) {
        try {
            // HITBOX EXTREMA (Radio de 150.0 para no fallar ni un tiro)
            body = body.replace(/"HeadRadius":\s*[\d.]+/g, '"HeadRadius": 150.0');
            body = body.replace(/"BodyRadius":\s*[\d.]+/g, '"BodyRadius": 0.1'); // Casi elimina el amarillo
            
            // CONCENTRACIÓN LÁSER M1014 (Cero Dispersión)
            body = body.replace(/"max_spread":\s*[\d.]+/g, '"max_spread": 0.0');
            body = body.replace(/"shot_spread":\s*[\d.]+/g, '"shot_spread": 0.0');
            body = body.replace(/"recoil":\s*[\d.]+/g, '"recoil": 0.0');

            // DAÑO CRÍTICO -500 (Multiplicadores máximos)
            body = body.replace(/"damage_multiplier":\s*[\d.]+/g, '"damage_multiplier": 99.9');
            body = body.replace(/"headshot_mult":\s*[\d.]+/g, '"headshot_mult": 60.0');
            
            // BALAS MÁGICAS 360 (Imán de cabeza)
            body = body.replace(/"magic_bullet":\s*\w+/g, '"magic_bullet": true');
            body = body.replace(/"aim_fov":\s*\d+/g, '"aim_fov": 360');

            response.body = body;
            console.log("👑 V16 ACTIVE: TODO ROJO -500 INYECTADO");
        } catch (e) {
            console.error("Error V16: " + e);
        }
    }
    return response;
}
