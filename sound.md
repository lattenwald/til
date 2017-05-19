# [Нормализация громкости звука](http://atzar.ru/ffmpeg-convert-mp3-and-normalize/)

    % ffmpeg -i input.wma -af "volumedetect" -f null /dev/null
    [Parsed_volumedetect_0 @ 0000000002b03b20] n_samples: 13738752
    [Parsed_volumedetect_0 @ 0000000002b03b20] mean_volume: -31.8 dB
    [Parsed_volumedetect_0 @ 0000000002b03b20] max_volume: -15.2 dB
    [Parsed_volumedetect_0 @ 0000000002b03b20] histogram_15db: 696
    [Parsed_volumedetect_0 @ 0000000002b03b20] histogram_16db: 78935

Обращаем внимание на `max_volume`, используем это в команде

    % ffmpeg -i input.wma -vn -ac 1 -ab 40K -af "volume=5dB" -f mp3 output.mp3
