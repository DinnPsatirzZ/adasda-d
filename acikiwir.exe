require('./semtinh')

// Dependencies
const { proto, generateWAMessage,areJidsSameUser } = require('@adiwajshing/baileys')
const fs = require('fs')
const util = require('util')
const chalk = require('chalk')
const moment = require('moment-timezone')
const { fetchJson, sleep } = require('./lib/myfunc')
const { say } = require('cfonts')
const { tebakbendera } = require('@bochilteam/scraper')

// Database
let tebaklagu = db.data.game.tebaklagu = []
let tebakgambar = db.data.game.tebakgambar = []
let tebakkata = db.data.game.tebakkata = []
let caklontong = db.data.game.lontong = []
let caklontong_desk = db.data.game.lontong_desk = []
let tebakkalimat = db.data.game.kalimat = []
let tebaklirik = db.data.game.lirik = []
let asahotak = db.data.game.asah = []
let tebakbenderaa = db.data.game.bendera = []
let tebaktebakan = db.data.game.tebakan = []
let kuismath = db.data.game.math = []

// DO NOT CHANGE
module.exports = dinn = async (dinn, m, chatUpdate) => {
    try {
        var body = (m.mtype === 'conversation') ? m.message.conversation : (m.mtype == 'imageMessage') ? m.message.imageMessage.caption : (m.mtype == 'videoMessage') ? m.message.videoMessage.caption : (m.mtype == 'extendedTextMessage') ? m.message.extendedTextMessage.text : (m.mtype == 'buttonsResponseMessage') ? m.message.buttonsResponseMessage.selectedButtonId : (m.mtype == 'listResponseMessage') ? m.message.listResponseMessage.singleSelectReply.selectedRowId : (m.mtype == 'templateButtonReplyMessage') ? m.message.templateButtonReplyMessage.selectedId : (m.mtype === 'messageContextInfo') ? (m.message.buttonsResponseMessage?.selectedButtonId || m.message.listResponseMessage?.singleSelectReply.selectedRowId || m.text) : ''
        var budy = (typeof m.text == 'string' ? m.text : '')
        var prefix = prefa ? /^[°•π÷×¶∆£¢€¥®™+✓_=|~!?@#$%^&.©^]/gi.test(body) ? body.match(/^[°•π÷×¶∆£¢€¥®™+✓_=|~!?@#$%^&.©^]/gi)[0] : "" : prefa ?? global.prefix
        const isCmd = body.startsWith(prefix)
        const command = body.replace(prefix, '').trim().split(/ +/).shift().toLowerCase()
        const args = body.trim().split(/ +/).slice(1)
        const pushname = m.pushName || "Unknown"
        const botNumber = await dinn.decodeJid(dinn.user.id)
        const isCreator = [botNumber, ...global.owner].map(v => v.replace(/[^0-9]/g, '') + '@s.whatsapp.net').includes(m.sender)
        const text = args.join(" ")
        const quoted = m.quoted ? m.quoted : m
        const mime = (quoted.msg || quoted).mimetype || ''
        const isMedia = /image|video|sticker|audio/.test(mime)
        const isPremium = isCreator || global.premium.map(v => v.replace(/[^0-9]/g, '') + '@s.whatsapp.net').includes(m.sender) || false

        try {
            let isNumber = x => typeof x === 'number' && !isNaN(x)
            let limitUser = isPremium ? global.limitawal.premium : global.limitawal.free
            let user = global.db.data.users[m.sender]
            if (typeof user !== 'object') global.db.data.users[m.sender] = {}
            if (user) {
                if (!isNumber(user.afkTime)) user.afkTime = -1
                if (!('afkReason' in user)) user.afkReason = ''
                if (!isNumber(user.limit)) user.limit = limitUser
            } else global.db.data.users[m.sender] = {
                afkTime: -1,
                afkReason: '',
                limit: limitUser,
            }

            let chats = global.db.data.chats[m.chat]
            if (typeof chats !== 'object') global.db.data.chats[m.chat] = {}
            if (chats) {
                if (!('mute' in chats)) chats.mute = false
                if (!('antilink' in chats)) chats.antilink = false
            } else global.db.data.chats[m.chat] = {
                mute: false,
                antilink: false,
            }

        } catch (err) {
            console.error(err)
        }

        if (m.message) {
            await dinn.sendPresenceUpdate('recording', m.chat)
            say(`MESSAGE\n\nremoteJid : ${m.isGroup ? pushname : 'Chat', `${m.chat}`}\npushName : ${m.pushName} (${m.sender})\ndate : ${moment(Date.now()).tz('Asia/Jakarta').locale('en').format('dddd, DD MMMM YYYY')}\ntext : ${(budy || m.mtype)}`, { 
                font: 'console', 
                align: 'left', 
                gradient: ['#DCE35B', '#45B649'], 
                transitionGradient: false 
              })}
        let cron = require('node-cron')
        cron.schedule('00 12 * * *', () => {
            let user = Object.keys(global.db.data.users)
            let limitUser = isPremium ? global.limitawal.premium : global.limitawal.free
            for (let jid of user) global.db.data.users[jid].limit = limitUser
        }, {
            scheduled: true,
            timezone: "Asia/Jakarta"
        })

        if (isMedia && m.msg.fileSha256 && (m.msg.fileSha256.toString('base64') in global.db.data.sticker)) {
            let hash = global.db.data.sticker[m.msg.fileSha256.toString('base64')]
            let { text, mentionedJid } = hash
            let messages = await generateWAMessage(m.chat, { text: text, mentions: mentionedJid }, {
                userJid: dinn.user.id,
                quoted: m.quoted && m.quoted.fakeObj
            })
            messages.key.fromMe = areJidsSameUser(m.sender, dinn.user.id)
            messages.key.id = m.key.id
            messages.pushName = m.pushName
            if (m.isGroup) messages.participant = m.sender
            let msg = {
                ...chatUpdate,
                messages: [proto.WebMessageInfo.fromObject(messages)],
                type: 'append'
            }
            dinn.ev.emit('messages.upsert', msg)
        }

        // Game Features

        if (tebaklagu.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebaklagu[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lagu', buttonText: { displayText: 'Tebak Lagu' }, type: 1 }], `Jawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebaklagu[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
    }

        if (tebakbenderaa.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebakbenderaa[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz bendera', buttonText: { displayText: 'Tebak Bendera' }, type: 1 }], `Jawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebakbenderaa[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
}
        if (asahotak.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = asahotak[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz otak', buttonText: { displayText: 'Asah Otak' }, type: 1 }], `Jawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete asahotak[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }
    
        if (tebakgambar.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebakgambar[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz gambar', buttonText: { displayText: 'Tebak Gambar' }, type: 1 }], ` Tebak Gambar \n\nJawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebakgambar[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (tebakkata.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebakkata[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz kata', buttonText: { displayText: 'Tebak Kata' }, type: 1 }], ` Tebak Kata \n\nJawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebakkata[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (caklontong.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = caklontong[m.sender.split('@')[0]]
            deskripsi = caklontong_desk[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lontong', buttonText: { displayText: 'Tebak Lontong' }, type: 1 }], ` Cak Lontong \n\nJawaban Benar 🎉\n*${deskripsi}*\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete caklontong[m.sender.split('@')[0]]
            delete caklontong_desk[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (tebakkalimat.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebakkalimat[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz kalimat', buttonText: { displayText: 'Tebak Kalimat' }, type: 1 }], ` Tebak Kalimat \n\nJawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebakkalimat[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (tebaklirik.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebaklirik[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lirik', buttonText: { displayText: 'Tebak Lirik' }, type: 1 }], ` Tebak Lirik \n\nJawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebaklirik[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (tebaktebakan.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = tebaktebakan[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
            await dinn.sendButtonText(m.chat, [{ buttonId: 'quiz tebakan', buttonText: { displayText: 'Tebak Tebakan' }, type: 1 }], ` Tebak Tebakan \n\nJawaban Benar 🎉\n\nIngin bermain lagi? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
            delete tebaktebakan[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        if (kuismath.hasOwnProperty(m.sender.split('@')[0]) && isCmd) {
            kuis = true
            jawaban = kuismath[m.sender.split('@')[0]]
            if (budy.toLowerCase() == jawaban) {
                await m.reply(`🎮 Kuis Matematika  🎮\n\nJawaban Benar 🎉\n\nIngin bermain lagi? kirim ${prefix}math mode`)
                delete kuismath[m.sender.split('@')[0]]
            } else m.reply('*Jawaban Salah!*')
        }

        this.game = this.game ? this.game : {}
        let room = Object.values(this.game).find(room => room.id && room.game && room.state && room.id.startsWith('tictactoe') && [room.game.playerX, room.game.playerO].includes(m.sender) && room.state == 'PLAYING')
        if (room) {
            let ok
            let isWin = !1
            let isTie = !1
            let isSurrender = !1
            if (!/^([1-9]|(me)?nyerah|surr?ender|off|skip)$/i.test(m.text)) return
            isSurrender = !/^[1-9]$/.test(m.text)
            if (m.sender !== room.game.currentTurn) {
                if (!isSurrender) return !0
            }
            if (!isSurrender && 1 > (ok = room.game.turn(m.sender === room.game.playerO, parseInt(m.text) - 1))) {
                m.reply({
                    '-3': 'Game telah berakhir',
                    '-2': 'Invalid',
                    '-1': 'Posisi Invalid',
                    0: 'Posisi Invalid',
                }[ok])
                return !0
            }
            if (m.sender === room.game.winner) isWin = true
            else if (room.game.board === 511) isTie = true
            let arr = room.game.render().map(v => {
                return {
                    X: '❌',
                    O: '⭕',
                    1: '1️⃣',
                    2: '2️⃣',
                    3: '3️⃣',
                    4: '4️⃣',
                    5: '5️⃣',
                    6: '6️⃣',
                    7: '7️⃣',
                    8: '8️⃣',
                    9: '9️⃣',
                }[v]
            })
            if (isSurrender) {
                room.game._currentTurn = m.sender === room.game.playerX
                isWin = true
            }
            let winner = isSurrender ? room.game.currentTurn : room.game.winner
            let str = `Room ID: ${room.id}\n\n${arr.slice(0, 3).join('')}\n${arr.slice(3, 6).join('')}\n${arr.slice(6).join('')}\n\n${isWin ? `@${winner.split('@')[0]} Menang!` : isTie ? `Game berakhir` : `Giliran ${['❌', '⭕'][1 * room.game._currentTurn]} (@${room.game.currentTurn.split('@')[0]})`}\n❌: @${room.game.playerX.split('@')[0]}\n⭕: @${room.game.playerO.split('@')[0]}\n\nKetik *nyerah* untuk menyerah dan mengakui kekalahan`
            if ((room.game._currentTurn ^ isSurrender ? room.x : room.o) !== m.chat)
                room[room.game._currentTurn ^ isSurrender ? 'x' : 'o'] = m.chat
            if (room.x !== room.o) await dinn.sendText(room.x, str, m, { mentions: parseMention(str) })
            await dinn.sendText(room.o, str, m, { mentions: parseMention(str) })
            if (isTie || isWin) {
                delete this.game[room.id]
            }
        }

        this.suit = this.suit ? this.suit : {}
        let roof = Object.values(this.suit).find(roof => roof.id && roof.status && [roof.p, roof.p2].includes(m.sender))
        if (roof) {
            let win = ''
            let tie = false
            if (m.sender == roof.p2 && /^(acc(ept)?|terima|gas|oke?|tolak|gamau|nanti|ga(k.)?bisa|y)/i.test(m.text) && m.isGroup && roof.status == 'wait') {
                if (/^(tolak|gamau|nanti|n|ga(k.)?bisa)/i.test(m.text)) {
                    dinn.sendTextWithMentions(m.chat, `@${roof.p2.split`@`[0]} menolak suit, suit dibatalkan`, m)
                    delete this.suit[roof.id]
                    return !0
                }
                roof.status = 'play'
                roof.asal = m.chat
                clearTimeout(roof.waktu)
                dinn.sendText(m.chat, `Suit telah dikirimkan ke chat\n\n@${roof.p.split`@`[0]} dan \n@${roof.p2.split`@`[0]}\n\nSilahkan pilih suit di chat masing"\nklik https://wa.me/${botNumber.split`@`[0]}`, m, { mentions: [roof.p, roof.p2] })
                if (!roof.pilih) dinn.sendText(roof.p, `Silahkan pilih \n\nBatu🗿\nKertas📄\nGunting✂️`, m)
                if (!roof.pilih2) dinn.sendText(roof.p2, `Silahkan pilih \n\nBatu🗿\nKertas📄\nGunting✂️`, m)
                roof.waktu_milih = setTimeout(() => {
                    if (!roof.pilih && !roof.pilih2) dinn.sendText(m.chat, `Kedua pemain tidak niat main,\nSuit dibatalkan`)
                    else if (!roof.pilih || !roof.pilih2) {
                        win = !roof.pilih ? roof.p2 : roof.p
                        dinn.sendTextWithMentions(m.chat, `@${(roof.pilih ? roof.p2 : roof.p).split`@`[0]} tidak memilih suit, game berakhir`, m)
                    }
                    delete this.suit[roof.id]
                    return !0
                }, roof.timeout)
            }
            let jwb = m.sender == roof.p
            let jwb2 = m.sender == roof.p2
            let g = /gunting/i
            let b = /batu/i
            let k = /kertas/i
            let reg = /^(gunting|batu|kertas)/i
            if (jwb && reg.test(m.text) && !roof.pilih && !m.isGroup) {
                roof.pilih = reg.exec(m.text.toLowerCase())[0]
                roof.text = m.text
                m.reply(`Kamu telah memilih ${m.text} ${!roof.pilih2 ? `\n\nMenunggu lawan memilih` : ''}`)
                if (!roof.pilih2) dinn.sendText(roof.p2, '_Lawan sudah memilih_\nSekarang giliran kamu', 0)
            }
            if (jwb2 && reg.test(m.text) && !roof.pilih2 && !m.isGroup) {
                roof.pilih2 = reg.exec(m.text.toLowerCase())[0]
                roof.text2 = m.text
                m.reply(`Kamu telah memilih ${m.text} ${!roof.pilih ? `\n\nMenunggu lawan memilih` : ''}`)
                if (!roof.pilih) dinn.sendText(roof.p, '_Lawan sudah memilih_\nSekarang giliran kamu', 0)
            }
            let stage = roof.pilih
            let stage2 = roof.pilih2
            if (roof.pilih && roof.pilih2) {
                clearTimeout(roof.waktu_milih)
                if (b.test(stage) && g.test(stage2)) win = roof.p
                else if (b.test(stage) && k.test(stage2)) win = roof.p2
                else if (g.test(stage) && k.test(stage2)) win = roof.p
                else if (g.test(stage) && b.test(stage2)) win = roof.p2
                else if (k.test(stage) && b.test(stage2)) win = roof.p
                else if (k.test(stage) && g.test(stage2)) win = roof.p2
                else if (stage == stage2) tie = true
                dinn.sendText(roof.asal, `_*Hasil Suit*_${tie ? '\nSERI' : ''}\n\n@${roof.p.split`@`[0]} (${roof.text}) ${tie ? '' : roof.p == win ? ` Menang \n` : ` Kalah \n`}\n@${roof.p2.split`@`[0]} (${roof.text2}) ${tie ? '' : roof.p2 == win ? ` Menang \n` : ` Kalah \n`}`.trim(), m, { mentions: [roof.p, roof.p2] })
                delete this.suit[roof.id]
            }
        }
        switch (command) {
            case 'menu': {
                if (!text) {
                let sections = 
                    [
                        {
                        title: "Minigames",
                        rows: [ 
                            {title: "Tebak Gambar 🏞️", rowId: "menu gambar"},
                            {title: "Tebak Lagu 🎵", rowId: "menu lagu"},
                            {title: "Tebak Kata 📄", rowId: "menu kata"},
                            {title: "Tebak Kalimat 📒", rowId: "menu kalimat"},
                            {title: "Tebak Lirik 🎧", rowId: "menu lirik"},
                            {title: "Tebak Bendera 🇮🇩", rowId: "menu bendera"},
                            {title: "Cak Lontong 🎭", rowId: "menu lontong"},
                            {title: "Asah Otak 🎓", rowId: "menu otak"},
                        ]
                    },
                    ]
                    dinn.sendListMsg(m.chat, `Tekan Untuk Melihat List Minigame Yang Tersedia`, 'Pop Chat\nBy Kelompok 4', `Halo ${m.pushName}`, `Klik Disini`, sections, m) }
                
                /*m.reply(`Example : ${prefix + command} lagu\n\nOption : \n1. lagu\n2. gambar\n3. kata\n4. kalimat\n5. lirik\n6.lontong`)*/
                if (args[0] === "lagu") {
                    if (tebaklagu.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://fatiharridho.github.io/tebaklagu.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    let msg = await dinn.sendMessage(m.chat, { audio: { url: result.link_song }, mimetype: 'audio/mpeg' }, { quoted: m })
                    dinn.sendText(m.chat, `Lagu Tersebut Adalah Lagu dari?\n\nArtist : ${result.artist}\nWaktu : 60s`, msg).then(() => {
                        tebaklagu[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                    })
                    await sleep(60000)
                    if (tebaklagu.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lagu', buttonText: { displayText: 'Tebak Lagu' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebaklagu[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete tebaklagu[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'gambar') {
                    if (tebakgambar.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/tebakgambar.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    dinn.sendImage(m.chat, result.img, `Silahkan Jawab Soal Di Atas Ini\n\nDeskripsi : ${result.deskripsi}\nWaktu : 60s`, m).then(() => {
                        tebakgambar[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                    })
                    await sleep(60000)
                    if (tebakgambar.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz gambar', buttonText: { displayText: 'Tebak Gambar' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebakgambar[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete tebakgambar[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'kata') {
                    if (tebakkata.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/tebakkata.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    dinn.sendText(m.chat, `Silahkan Jawab Pertanyaan Berikut\n\n${result.soal}\nWaktu : 60s`, m).then(() => {
                        tebakkata[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                    })
                    await sleep(60000)
                    if (tebakkata.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz kata', buttonText: { displayText: 'Tebak Kata' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebakkata[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete tebakkata[m.sender.split('@')[0]]
                    }
                
                    } else if (args[0] === 'kalimat') {
                    if (tebakkalimat.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/tebakkalimat.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    dinn.sendText(m.chat, `Silahkan Jawab Pertanyaan Berikut\n\n${result.soal}\nWaktu : 60s`, m).then(() => {
                        tebakkalimat[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                    })
                    await sleep(60000)
                    if (tebakkalimat.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz kalimat', buttonText: { displayText: 'Tebak Kalimat' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebakkalimat[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete tebakkalimat[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'lirik') {
                    if (tebaklirik.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/tebaklirik.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    dinn.sendText(m.chat, `Ini Adalah Lirik Dari Lagu? : *${result.soal}*?\nWaktu : 60s`, m).then(() => {
                        tebaklirik[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                    })
                    await sleep(60000)
                    if (tebaklirik.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lirik', buttonText: { displayText: 'Tebak Lirik' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebaklirik[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete tebaklirik[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'lontong') {
                    if (caklontong.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                    let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/caklontong.json')
                    let result = anu[Math.floor(Math.random() * anu.length)]
                    dinn.sendText(m.chat, `*Jawablah Pertanyaan Berikut :*\n${result.soal}*\nWaktu : 60s`, m).then(() => {
                        caklontong[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                        caklontong_desk[m.sender.split('@')[0]] = result.deskripsi
                    })
                    await sleep(60000)
                    if (caklontong.hasOwnProperty(m.sender.split('@')[0])) {
                        console.log("Jawaban: " + result.jawaban)
                        dinn.sendButtonText(m.chat, [{ buttonId: 'quiz lontong', buttonText: { displayText: 'Tebak Lontong' }, type: 1 }], `Waktu Habis\nJawaban:  ${asahotak[m.sender.split('@')[0]]}\nDeskripsi : ${caklontong_desk[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                        delete caklontong[m.sender.split('@')[0]]
                        delete caklontong_desk[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'otak') {
                        if (asahotak.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                        let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/asahotak.json')
                        let result = anu[Math.floor(Math.random() * anu.length)]
                        dinn.sendText(m.chat, `*Jawablah Pertanyaan Berikut :*\n${result.soal}*\nWaktu : 60s`, m).then(() => {
                            asahotak[m.sender.split('@')[0]] = result.jawaban.toLowerCase()
                        })
                        await sleep(60000)
                        if (asahotak.hasOwnProperty(m.sender.split('@')[0])) {
                            console.log("Jawaban: " + result.jawaban)
                            dinn.sendButtonText(m.chat, [{ buttonId: 'quiz otak', buttonText: { displayText: 'Asah Otak' }, type: 1 }], `Waktu Habis\nJawaban:  ${asahotak[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                            delete asahotak[m.sender.split('@')[0]]
                    }
                    } else if (args[0] === 'bendera') {
                        if (tebakbenderaa.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                        let anu = await fetchJson('https://raw.githubusercontent.com/BochilTeam/database/master/games/tebakbendera2.json')
                        let result = anu[Math.floor(Math.random() * anu.length)]
                        dinn.sendImage(m.chat, result.img, `Sebutkan Nama Negara Diatas Ini !\nWaktu : 60s`, m).then(() => {
                            tebakbenderaa[m.sender.split('@')[0]] = result.name.toLowerCase()
                        })
                        await sleep(60000)
                        if (tebakbenderaa.hasOwnProperty(m.sender.split('@')[0])) {
                            console.log("Jawaban: " + result.name)
                            dinn.sendButtonText(m.chat, [{ buttonId: 'quiz bendera', buttonText: { displayText: 'Tebak Bendera' }, type: 1 }], `Waktu Habis\nJawaban:  ${tebakbenderaa[m.sender.split('@')[0]]}\n\nIngin bermain? tekan button dibawah`, 'Pop Chat\nBy Kelompok 4', m)
                            delete tebakbenderaa[m.sender.split('@')[0]]
                    }
                }
            }
            break
            case 'kuismath': case 'math': {
                if (kuismath.hasOwnProperty(m.sender.split('@')[0])) throw "Masih Ada Sesi Yang Belum Diselesaikan!"
                let { genMath, modes } = require('./src/math')
                if (!text) throw `Mode: ${Object.keys(modes).join(' | ')}\nContoh penggunaan: ${prefix}math medium`
                let result = await genMath(text.toLowerCase())
                dfxz.sendText(m.chat, `*Berapa hasil dari: ${result.soal.toLowerCase()}*?\n\nWaktu: ${(result.waktu / 1000).toFixed(2)} detik`, m).then(() => {
                    kuismath[m.sender.split('@')[0]] = result.jawaban
                })
                await sleep(result.waktu)
                if (kuismath.hasOwnProperty(m.sender.split('@')[0])) {
                    console.log("Jawaban: " + result.jawaban)
                    m.reply("Waktu Habis\nJawaban: " + kuismath[m.sender.split('@')[0]])
                    delete kuismath[m.sender.split('@')[0]]
                }
            }
            break
            case 'dinn': {
                dinn.sendTextWithMentions(m.chat, '@6287819654911', m)
                await sleep(3000)
                dinn.sendTextWithMentions(m.chat, `@${m.sender.split('@')[0]} Keren juga luwh nemu easter egg`)
            }
            default:
                if (budy.includes('Assalamualaikum')) {
                    throw ('Waalaikumsalam')
                }
                if (budy.includes('Asalamualaikum')) {
                    throw ('Waalaikumsalam')
                }


                if (isCmd && budy.toLowerCase() != undefined) {
                    if (m.chat.endsWith('broadcast')) return
                    if (m.isBaileys) return
                    let msgs = global.db.data.database
                    if (!(budy.toLowerCase() in msgs)) return
                    dinn.copyNForward(m.chat, msgs[budy.toLowerCase()], true)
                }
        }


    } catch (err) {
        dinn.sendText('6287819654911@s.whatsapp.net', util.format(err), m)
    }
}


let file = require.resolve(__filename)
fs.watchFile(file, () => {
    fs.unwatchFile(file)
    console.log(chalk.redBright(`Update ${__filename}`))
    delete require.cache[file]
    require(file)
})
