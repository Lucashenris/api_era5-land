# Download data Era5-Land

Esse script é utilizado para baixar dados do era5-land de forma automática.

- Para a importação e uso correto da biblioteca cdsapi, é necessária uma configuração prévia disponibilizada em: https://cds.climate.copernicus.eu/api-how-to


```python
import cdsapi

c = cdsapi.Client()
variaveis = ['surface_solar_radiation_downwards',
             '10m_u_component_of_wind', '10m_v_component_of_wind',
             '2m_temperature', 'surface_pressure', 'total_precipitation', '2m_dewpoint_temperature']

meses = ['01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11', '12']

anos = ['2000', '2001', '2002', '2003', '2004', '2005', '2006', '2007', '2008', '2009', '2010',
        '2011', '2012', '2013', '2014', '2015', '2016', '2017', '2018', '2019', '2020', '2021',
        '2022']

for variavel in variaveis:
    for mes in meses:
        for ano in anos:
            c.retrieve(
                'reanalysis-era5-land',
                {
                    'variable': variavel,
                    'year': ano,
                    'month': mes,
                    'day': [
                        '01', '02', '03',
                        '04', '05', '06',
                        '07', '08', '09',
                        '10', '11', '12',
                        '13', '14', '15',
                        '16', '17', '18',
                        '19', '20', '21',
                        '22', '23', '24',
                        '25', '26', '27',
                        '28', '29', '30',
                        '31',
                    ],
                    'time': [
                        '00:00', '01:00', '02:00',
                        '03:00', '04:00', '05:00',
                        '06:00', '07:00', '08:00',
                        '09:00', '10:00', '11:00',
                        '12:00', '13:00', '14:00',
                        '15:00', '16:00', '17:00',
                        '18:00', '19:00', '20:00',
                        '21:00', '22:00', '23:00',
                    ],
                    'area': [
                        -18.87, -52.33, -23.57,
                        -46.83,
                    ],
                    'format': 'netcdf.zip',
                },
                f'{variavel}_{mes}_{ano}.zip')
```
