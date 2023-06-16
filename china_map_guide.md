### 实际使用指南

1. wahoomc/setup_functions.py
 - 在实际运行过程中，通过选择注释掉三处delete_o5m_pbf_files_in_folder，避免反复下载
2. wahoomc/osm_maps_functions.py
 - 在525行 generate_elevation(self, use_srtm1) 函数中，首次运行可以在cmd中增加 “--download-only only download needed files, don't write contour data.” 以避免因下载问题导致的程序终端
 - 全部下载完成后，删除--download-only，重新运行
 - 可以注释掉“if not (len(out_file_elevation_existing) == 1 and os.path.isfile(out_file_elevation_existing[0])) \
                    or self.o_osm_data.force_processing is True:” 保证每次contour 重新计算
 - 考虑生成contour的时间效率，可以同时运行多个，方法是修改generate_elevation(self, use_srtm1) 函数中循环的起始值。另外，将主程序文件夹wahooMapsCreator 以及 数据文件夹 wahooMapsCreatorData 复制在相同目录并重命名，修改constants.py中 “USER_WAHOO_MC = os.path.join(str(Path.home()), 'wahooMapsCreatorData')” 中数据文件夹的路径
 - 最后将生成的两个数据文件夹合并
3. 在下载china.osm.pdf的时候可以在程序中打印下载路径，通过wget的方式自行下载，然后复制到/wahooMapsCreatorData/_download/maps 下面。
